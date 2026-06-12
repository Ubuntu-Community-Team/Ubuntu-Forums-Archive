---
title: "Nvidia GTX 275 gtx 275 owner's thread"
date: 2009-07-11
forum: Hardware
---

### Post by jonboy99 on 2009-07-11
I have started this thread so anyone with a gtx 275 can subscribe to it and update if and when the linux drivers are produced by nvidia for this card, and it becomes usable in ubuntu with the nvidia drivers.

By putting this entry into the xorg.conf file it is at least possible to boot into X with the full screen resolution available:

(from [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy))

Section "Device"
Identifier "Card0"
BoardName "Generic Geforce GTX275"
Driver "nv"
EndSection

but obviously things will be much improved when full hardware support is available.  

So please post here if and when you find a fix!

Jon

---

### Post by fede on 2009-07-16
In case it matters, I am using nvidia drivers with no problems under archlinux. I read somewhere an answer by an nvidia representative where he stated that the drivers should work with the 275, regardless of it not being in the list of supported cards. And for me it does.

Check this out:
[http://bbs.archlinux.org/viewtopic.php?id=75030]("http://bbs.archlinux.org/viewtopic.php?id=75030")

---

### Post by jonboy99 on 2009-07-16
Thanks fede, good to know it works.  Unfortunately I don't know enough about linux to translate your steps into suitable ones for ubuntu, but hopefully someone will post a dummy's guide soon!

> **fede said:**
> In case it matters, I am using nvidia drivers with no problems under archlinux. I read somewhere an answer by an nvidia representative where he stated that the drivers should work with the 275, regardless of it not being in the list of supported cards. And for me it does.

Check this out:
[http://bbs.archlinux.org/viewtopic.php?id=75030]("http://bbs.archlinux.org/viewtopic.php?id=75030")

---

### Post by fede on 2009-07-18
It also works fine under Kubuntu, I have a pretty much default installation. In any case, here's an ubuntu step by step procedure:

1. Print or write down these steps as you will need to shut down X (ie the graphic interface) to modify /etc/X11/xorg.conf (where all of X's configs are stored), so you will have no browser to read this. Also, save your work and close open programs if you're working on something, obviously.

2. Press Ctrl + Alt + F1 to go to the first text terminal. Login with your username and password

3. ```
sudo /etc/init.d/gdm stop
``` to stop X (if you use gnome). If you use Kubuntu: ```
sudo /etc/init.d/kdm stop
```.

4. ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.my_backup
``` to backup your current xorg.conf settings, in case there's something there you need (ie touchpad config, or some other special setting), since we will create a new xorg.conf from scratch.

5. ```
sudo X -configure :1
``` creates a new xorg.conf, stored in your home directory

6. ```
sudo mv /home/YOUR_USERNAME_HERE/xorg.conf.new /etc/X11/xorg.conf
``` to move xorg.conf to where it will be the active X configuration. Obviously replace YOUR_USERNAME_HERE with your actual username.

7. ```
sudo /etc/init.d/gdm start
``` to start X again. replace gdm with kdm if you use Kubuntu.

---

### Post by jonboy99 on 2009-07-18
Ah, I didn't realise those steps were just to create a new xorg.conf and then copy it into the right place.   
I was about to try your steps, and didn't know if I needed to install the hardware drivers first, so I did this through the system menu, and when I rebooted all was working!  So looks like the ubuntu staff have sorted whatever was wrong with the install process out.  This is using the 180 driver too.
Anyway, sorted now, thanks for the help.

Jon

(PS on intrepid for anyone who wants to know.)

---

### Post by ZDemon on 2009-09-11
The 190.32 Beta drivers officially support this card.

Can anyone post a step by step tutorial on how to install NVidias .run package in Ubuntu? I tried it, but my screen becomes blank (no signal).

Why is this so difficult. Do we need to include a modalias to allow ubuntu to detect this card model?

---

### Post by ManFromMars on 2009-09-15
I just built a new PC with a GTX 275, running Ubuntu 9.04 64-bit. I just installed the nvidia-glx-180 package from Synaptic (and dependent packages), enabled the driver in System->Administration->Hardware Drivers, restarted and everything seems to work fine. It's recognised my Dell S2409W monitor, too. Currently having trouble installing Half-Life 2 for testing it out properly, but Tux Racer was running nicely :-D

---

### Post by DianJoubert.com on 2009-09-24
> **ManFromMars said:**
> I just built a new PC with a GTX 275, running Ubuntu 9.04 64-bit. I just installed the nvidia-glx-180 package from Synaptic (and dependent packages), enabled the driver in System->Administration->Hardware Drivers, restarted and everything seems to work fine. It's recognised my Dell S2409W monitor, too. Currently having trouble installing Half-Life 2 for testing it out properly, but Tux Racer was running nicely :-D

Thank You for the post. I quickly and easily installed the driver this way.:P

---

### Post by John Rivera on 2010-01-08
I am thinking of upgrading my graphics and this is top option at the moment, but how is driver support currently ?

Nearly out of box (install and such things to do as well) working or does it still need extensive configuration to get running ?

---

### Post by jonboy99 on 2010-01-08
I think it's plug and play - in the end mine just worked, so i think they sorted the install process out.

---

### Post by John Rivera on 2010-01-10
Good to know since I want to get rid of my passive cooled GF7600 GF card for gaming use, does not work well in that.

---

### Post by John Rivera on 2010-03-28
Funny.

I did read these
[http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-mainstream-quality-update-3/3DMark06-v1.1.0-3DMark-Score,1666.html](http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-mainstream-quality-update-3/3DMark06-v1.1.0-3DMark-Score,1666.html) and
[http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-high-quality-update-3/3DMark06-v1.1.0-3DMark-Score,1697.html](http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-high-quality-update-3/3DMark06-v1.1.0-3DMark-Score,1697.html)

only to notify that it seems that 275 would be best bang per invested € at the moment (atleast charts seem to be so for me) although this might be just local thing.

Anyways makes me think even more of getting this card :D:popcorn:

---

### Post by ryandward on 2011-04-23
Is this problem still not fixed? Please help, there are too many threads that say too many things, and I am going crazy trying to make my graphics card work.:popcorn:

---

