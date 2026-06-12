---
title: "how to share folder over the internet"
date: 2008-09-16
forum: General Help
---

### Post by micks80 on 2008-09-16
Hi Friends,
I am able to share a folder on a linux computer using samba and access it from a windows box on the same network.

But can someone pls tell me how to access it over the internet???

Thanks

---

### Post by mb_webguy on 2008-09-16
If you're behind a router, it can be difficult -- though no different than if you wanted to access a shared folder on Windows from the Internet.

The best way in my opinion would be to set up a web server or ftp server on your Ubuntu machine, and then set up port forwarding on your router.  These are the usual ways of sharing files over the Internet.  An ftp server is better than a web server if you want to restrict who has access to the files. 

If you're sure you want to share using Samba, then you need to set port forwarding on your router for your Ubuntu machine on ports 137-139.  (Note:  I *think* this should work, in theory, but I've never tried it.)  If you can post the make and model of your router, I can walk you through setting up port forwarding.

---

### Post by micks80 on 2008-09-16
Thanks webguy,
I dont necessarily need samba,i can go ftp like you suggested. I have ftp installed but i don't know how to create a folder for it or add users to it,so i thought samba would be easier.

I will see if i can find something on google or if you can send me a good link for ftp.

Thanks

---

### Post by mb_webguy on 2008-09-16
Google "vsftpd" or "ubuntu vsftpd", and you should find some good information about installing and configuring vsftpd (the Very Secure FTP Daemon).

"sudo apt-get install vsftpd" will give you a default installation, which allows full download access for anonymous users.  You'll have to configure vsftpd to allow things like user login and write access.

---

### Post by Breakar on 2008-09-16
Anther way, is you could use a torrent and torrent the whole folder.

---

