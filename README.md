# docker-hidden-sftp

```docker pull yangzhaofengsteven/hidden-sftp```

```
docker run -itd \
	--name=hidden-sftp \
	-e FTP_USER=<user name> \
	-e HIDDEN_SERVICE_PORT=<default is 22> \
	-v /srv/docker/hidden-sftp/home:/home \
	-v /srv/docker/hidden-sftp/service:/var/lib/tor/hidden_service \
	yangzhaofengsteven/hidden-sftp
```

You may need to manually modify the permission of ```/srv/docker/hidden-sftp/service```

Original password of ftp user is empty. Using pubkey auth method is recommended. Please edit ```/srv/docker/hidden-sftp/home/$FTP_USER/.ssh/authorized_keys```

Local Usage:
```sftp -o ProxyCommand='nc -X 5 -x 127.0.0.1:9150 %h %p' <user name>@<geneted server name>.onion```
where ```nc``` is ```netcat-openbsd```
