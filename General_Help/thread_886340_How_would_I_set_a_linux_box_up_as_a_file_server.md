---
title: "How would I set a linux box up as a file server?"
date: 2008-08-11
forum: General Help
---

### Post by shamusl on 2008-08-11
I have no idea how, but I want to give a few files to a few friends directly from my IP address to them (avoiding storage sites), does anybody have any simple, temporary ideas. (Something I can turn on and off would be nice).

---

### Post by hyper_ch on 2008-08-11
simplest way would be to setup a ssh server, create user accounts and then have them login through sftp (e.g. with [http://www.winscp.com](http://www.winscp.com) ). However they could play around your system so maybe you want to jail them with "mysecureshell".

Another approache is, if they just need to be able to download and not upload to setup apache and limit access by using .htaccess and setup according dirs.

Or you could setup a ftp server.

Or you could also use samba...

If you're behind a router you will ahve to port-forward the according ports for any approach from your router to your computer.

---

