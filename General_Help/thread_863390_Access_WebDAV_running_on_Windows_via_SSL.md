---
title: "Access WebDAV running on Windows via SSL"
date: 2008-07-18
forum: General Help
---

### Post by MountainX on 2008-07-18
I want to access a WebDAV (IIS) server running on a Windows host that requires an SSL connection. I'm running Hardy. I tried the approach I thought would be easy -- using Nautilus -- but I couldn't get it to work.
Error:
```
Couldn't display "dav://myuser@theserver.com:443/".

Error: HTTP Error: Connection terminated unexpectedly
Please select another viewer and try again.
```

I also tried:
```
sshfs www.theserver.com: /media/mymount/
```
Response:
```
read: Connection reset by peer

```

EDIT: I can connect to the WebDAV server from IE in Windows. Can also access the server via HTTPS in Firefox. Just can't get WebDAV or sshfs access from Ubuntu to work.

My ultimate goal is to set up Foxmarks to point to the WebDAV server:
[http://wiki.foxmarks.com/wiki/Foxmarks:_Frequently_Asked_Questions#Can_I_use_Foxmarks_with_my_own_server.3F](http://wiki.foxmarks.com/wiki/Foxmarks:_Frequently_Asked_Questions#Can_I_use_Foxmarks_with_my_own_server.3F)

Any suggestions? Thanks.

---

