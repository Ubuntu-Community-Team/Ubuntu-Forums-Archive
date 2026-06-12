---
title: "ftp localhost"
date: 2008-07-27
forum: General Help
---

### Post by GNVJayprakash on 2008-07-27
Hi,
     I have installed Ubuntu 8.04 over Windows XP OS as an application. On logging in to the Ubuntu and trying **ftp localhost**, I am getting a **connect: refused** error.

As both the OS are installed on the same system. What could the error be?

Thanks,
JPrakash

---

### Post by enchance on 2008-07-27
Why are you trying to ftp to localhost when you could just copy files directly? Anyway, try checking to see if apache is loaded at runtime. This can be done by typing "localhost" in your browser. If nothing came out either check your sessions to see if it loads upon restarting or better yet reinstall the whole thing. :)

Also, a good alternative to bash ftp is ncftp. It's so good I never had to go back to simple ftp ever since.
```
sudo apt-get install ncftp
```

The easiest and best way to install LAMP without breaking a sweat is through Synaptic. Open Synaptic and go to Edit->Mark Packages by Task->LAMP server

---

### Post by Keith Hedger on 2008-07-27
u need to be running a ftp server try:```
sudo apt-get install ftpd
```

---

