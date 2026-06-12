---
title: "Can't Start X,  Graphics Card Not Found?"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by squimmy on 2006-07-31
Hello,

I am trying to install ubuntu. Or, even just get into the ubuntu live CD. Unfortunately, when the cd loads, it can't start X. I can't remember the exact message but it said something about device not found and X can't start.

Something like this happened in pclinuxos, I had to set the display driver to fglrx to get it to work.

I have a rather strange ati card I suppose... my exact card is a ati x800 gto².


Anyway, does anyone know how I can get X started?

Thanks a lot for any help!

---

### Post by Paerez on 2006-07-31
Have you tried the CD's safe mode? Then once it's installed you can boot it in the command line and set the driver to fglrx.

---

### Post by squimmy on 2006-08-01
Accepting the risk of sounding like an idiot, i'm going to ask an embarassing question. How do I change the driver to fglrx? 

I know how to do it in pclinuxos but I presume it is very much different in ubuntu.

Thanks.

---

### Post by Paerez on 2006-08-01
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

```
that's it. Then if you are logged in, logout and press CTRL+ALT+BACKSPACE. If you are just at the command line, run:
```
sudo /etc/init.d/gdm restart
```

---

### Post by squimmy on 2006-08-01
That leads to another more embarassing question.

Sudo requires the root password, right? Well what the hell is the root password that is set initially in ubuntu?



Thanks

---

### Post by Paerez on 2006-08-01
su requires the root password, sudo asks for your password and then gives you root power. Just put your password in :D

---

### Post by squimmy on 2006-08-01
Then what is my password? The one that ubuntu logs in with on the live cd? The default one.



Or have I completely missed a step between downloading and using the live cd?

Thanks.

---

### Post by Paerez on 2006-08-01
if you are running the livecd, sudo won't ask for a password. Just run the commands, then come back and ask questions if you have any.

---

