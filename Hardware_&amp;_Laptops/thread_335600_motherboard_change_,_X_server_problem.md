---
title: "motherboard change , X server problem"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by Krist Blomme on 2007-01-10
Hi

I have a running ubuntu system , however , I'm changing my mother board .
so ,I have move the hard-drive and graphic-card to the new mother board .

When the system starts the xServer doesn't start , I get following message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly; Would you like to view the x-server output to diagnose .....

If I use the live CD (what I'm doing now) graphics is OK .
Can someone advise how I can reconfigure the XServer ?
Can I copy configuration from the live CD boot to the hard=drive ?

greetings
Krist

---

### Post by r4ik on 2007-01-10
sudo dpkg-reconfigure xserver-xorg

Follow the defaults,

sudo /etc/init.d/gdm restart

and you should be oke.

Good luck.

---

### Post by Krist Blomme on 2007-01-11
tnx for the advise .

but the reconfiguration asked me things that I couldn't find out , 
e.g. I don't know the brand of the video card anymore , 
at the end the LCD display complained that it had bad configuration.
So obviously I took the wrong options.

I finally booted the live CD again , mounted the hard drive and copied the 
/etc/X11/xorg.conf file from the live CD environment to the hard drive.

I'm back in business now  

greetings
Krist

---

