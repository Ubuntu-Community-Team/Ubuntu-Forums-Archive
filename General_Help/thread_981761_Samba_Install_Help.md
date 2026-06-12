---
title: "Samba Install Help"
date: 2008-11-14
forum: General Help
---

### Post by _Craig_ on 2008-11-14
Just a quick one (i hope).

I have a ubuntu machine that I want to connect to the windows domain, so i need samba.
I cant install samba from the package manager because the machine is not on the internet.

I downloaded samba 3.2.4.tar.gz from the net, but i dont know how to install it.

note:I am very very new to Linux, very.


Craig:guitar:

---

### Post by daximus on 2008-11-14
Samba packages should be on your installation CD.  Put it in the drive, go into "Software Sources" and make sure it's enabled, then run Synaptic and install samba.

---

### Post by _Craig_ on 2008-11-14
Thanks, seems to be installed because in the package manager the only options i have for samba is to remove it.
But now i cant find the program to run it! Im really bad at this, its not in applications.
How do I run it?

---

### Post by Iowan on 2008-11-14
There are two parts to Samba - the client is usually pre-installed, the server must be added afterward. If you need the server and if it is installed, **/etc/init.d/samba start** should do it. I don't have the server on this workstation - this is what happens:```
user1@workstation:~$ /etc/init.d/samba start
bash: /etc/init.d/samba: No such file or directory

```

---

### Post by bab1 on 2008-11-14
If Samba (server) is installed correctly it should start when the computer is booted up.  To check if it is running try:```
ps -ef|grep  mbd
```  This should have 2 instances of [COLOR="Red"]**smbd**[/COLOR] and 1 of [COLOR="Blue"]**nmbd**[/COLOR].

---

