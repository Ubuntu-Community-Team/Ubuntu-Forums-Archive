---
title: "Ubuntu 9.04 Minimal Install No Desktop"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Gemu on 2009-08-12
Greetings, I am having trouble with the minimum install ubuntu 9.04. It may be cause I used ubuntu 9.04 instead of what the tutorial suggested over at Psychocats. 

I have it installed on a 2nd HD in a 2001 gateway 600mghz, 512 RAM and it boots fine to a command line only situation. I cant seem to get the desktop going no matter what I do. Am I going to have to use an older version?

 I like 9.04 because it automatically detects my linksys usb wireless adapter and has the NetworkManager Applet 0.7.0.100 just like the live cd.

---

### Post by Aubergines on 2009-08-12
That'll be because the minimal install is commandline only. You can however use it as a base to install xorg and one of the lighter weight window managers.

---

### Post by samser on 2009-08-12
how do you uninstall? something like reverse sudo apt-get install (thing) ???

---

### Post by Aubergines on 2009-08-12
> **samser said:**
> how do you uninstall? something like reverse sudo apt-get install (thing) ???

Is that in any way related to the original post? You can remove packages with the remove or purge switch. So:
```
apt-get remove (thing)
```
For more details type:
```
man apt-get
```
```
apt-get --help
```

---

### Post by zvacet on 2009-08-12
@ **Gemu**


[Here]("https://help.ubuntu.com/community/Installation/LowMemorySystems") is a guide how to install xorg and window manager after minimal install.

---

### Post by slakkie on 2009-08-12
I think installing xdm only will already supply you with the correct xorg packages. But could be wrong..

---

### Post by Gemu on 2009-08-12
Thanks for the replys. I downloaded and installed the minimum 9.04 Ubuntu CD and all I have is a command line. It took most of the day to install it on that slow machine and it still got the partitions wrong. I had to copy the root file system over from a 3rd (too small) partition that I never asked to be created to the first Partition that I asked for, edit grub and fstab so it would boot. 

 So far the only good that has come from it is finding out how to boot linux in that old pc oh and having grub installed, love that grub man. 

While it was installing I was watching the info come across the sreen and right where every other linux cd failed to boot--- trying to disable IRQ 10---, the ubuntu installer said, " IRQ 10 no one cared, try irqpoll" and just zoomed on by that IRQ 10 pest. It was just what I needed to get the latest Puppy421 booting on the machine and move a few things around and repartition my HD. 

 I like Ubuntu because it tends to be the most stable of all. If your copying your Hd you dont usually have to worry about it locking up on you. Plus I like to use the command line instead of having a gui for every little thing. 

 A desktop would be nice though. I have installed all kind of apps as suggested in psychocats tutorial and tryed /etc/init.d/xdm start and a few others but nothing happens.

---

### Post by Gemu on 2009-08-26
After attempting to start gdm, xdm or anything else I've tryed, I get an error on the screen -

 no vesa module found

 Is there a way that I can get that driver installed? I really want to get Ubuntu up and running on my old machine.

---

