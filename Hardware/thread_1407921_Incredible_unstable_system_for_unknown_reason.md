---
title: "Incredible unstable system for unknown reason"
date: 2010-02-15
forum: Hardware
---

### Post by kubu88 on 2010-02-15
Well, it' s very hard to try to describe use my situation..it's so critic as I am writing from a win7 partition. What I have done:
1) New PC has arrived at home.
2)Take Ubuntu 9.10 DVD and make a fresh installation on a free and pre-formatted hard drive.
3) Installation complete. 
4) Run the system...the risolution of the monitor sucks..too low for my 24'' LCD so i decided to install nvidia driver. 
5) Install nvidia driver and system freeze. Seems like it was doing lots of process. 
6)Reboot. ok a bit more stable...open firefox and watch a youtube clip and FREEZE!AGAIN. After reboot and reboot. The system definitely died at the last reboot with a black screen.
7)New installation. After that I decided to not install NVIDIA driver and try to find out the reason but i thought it was a conflict with free driver..so purge the and let another chanche to the closed one. Nothing..system freeze again and this time audio was influenced 'cause when i play something it sound with lots of rustling and noise.

I hope you can help. I think the problem is this driver. My graphic card is Geforce 8200, ubuntu 9.10 32 bit

---

### Post by kubu88 on 2010-02-16
please up

---

### Post by dE_logics on 2010-02-16
These are standard procedures.

> You need to reconfigure X server.

Press alt+cntrl+F2

Login with your username and passwd (you will not see the password being typed).

Run - 

```
sudo /etc/init.d/gdm stop
```

Then run - 

```
sudo Xorg -configure
```

```
cp /home/<your user name>/xorg.conf.new /etc/X11/xorg.conf
```

```
/etc/init.d/gdm start
```

However you NEED to install the Nvidia drivers and make it work... The opensource drivers are pathetic.

Why not contact nvidia support for this?

---

### Post by kubu88 on 2010-02-16
should I make that before or after the installation of Nvidia driver?

---

