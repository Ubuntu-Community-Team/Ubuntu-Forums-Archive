---
title: "How to uninstall all fglrx and install xorg"
date: 2009-05-03
forum: Hardware
---

### Post by gaalaaant on 2009-05-03
unninstall all fglrx and install the free drivers. xserver-xorg-video-ati and xserver-xorg-video-radeon was the advice I got somewhere else.  How do I do that?

---

### Post by mikedep333 on 2009-05-03
Just use the restricted drivers manager (under system, administration) and deselect the Restricted ATI driver (FGLRX.)

Please list what version of Ubuntu you are running if this does not work.

---

### Post by gaalaaant on 2009-05-03
I am running Jaunty off of an upgrade from Intrepid.  Gfx were fin in intrepid.  Will post later if it worked ( at work now :()

---

### Post by gaalaaant on 2009-05-03
Yeah I used the "Hardware Drivers" thing under administration and it told me that I have no proprietary drivers on my machine.

---

### Post by asuastrophysics on 2009-05-03
I don't have X running. It won't run. Activating ATI drivers under hardware manager broke it. Now I need to get rid of fglrx from shell

to do that i did 
```
sudo apt-get remove xorg-driver-fglrx
```
It worked, but I still have no desktop. 
How do I completely remove this broken driver? 
what other command do i need to issue? 
If there is no other command, how do i initialize the open source driver? is there a command for that?

---

### Post by mikedep333 on 2009-05-04
Try running:

```
sudo dpkg-reconfigure xserver-xorg
```

You'll then need to restart the X server (or GDM.)

---

