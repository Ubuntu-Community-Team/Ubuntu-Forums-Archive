---
title: "Webcam help"
date: 2008-08-07
forum: General Help
---

### Post by Viridia on 2008-08-07
So I have a webcam, and I use camorama. I want to be able to take pictures from it from a different computer. I have no idea how to set up an FTP server. I could use the ubuntu box as a server, I guess. It has light system specs, but only one person would be accessing this, and that would only happen rarely. Any advice?

Thanks

---

### Post by phidia on 2008-08-07
Ubuntu wiki [ftp server setup]("https://help.ubuntu.com/community/FtpServer").
Is that what you're looking for? Hope that helps.

---

### Post by cariboo on 2008-08-07
If you don't want to go to the trouble of setting up an ftp server, install ssh. Openssh-server on the computer you want to get the pictures from and just ssh on the computer you want to download  to. then once it it installed and setup just open nautilus (Places-->Home folder) click on the toggle button on the far left to get a location bar then enter in the location bar:

 ```
sftp://<user>@<remote computer>
```

Where <user> is your user name and <remote computer> is the name of your remote computer. Make sure the name and ip address of the remote computer is in /etc/hosts.

Jim

---

