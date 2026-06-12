---
title: "Newbie installation fail"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by lordmonkeyu on 2009-09-22
Hello, 
I wanted to give ubuntu a shoot and installed it on my computer after taking a look on LiveCD. But after intallation instead of having great ubuntu 9.04 running I have console (like DOS) on black screen and all I can do is insert my login, password and insert commands (which I obviously don't know YET).
There is also a warning about that my graphics card is not supported (nvidia geforce 8600m gt) and it will run in low video mode( I can also choose there to go to console).
What should I do about that?

---

### Post by scragar on 2009-09-22
You can install things from the command line still, try installing envy and running that to install your graphics driver:
```
sudo -i
apt-get install envyng-core
envyng -t
```
This will make your root for a short while(to let you install applications), install envy, then run envy and allow you to choose to install/uninstall the closed source drivers provided by Nvidia without having to search for those drivers manually.

Once it's done you'll need to restart(not actually true, but it's much easier than doing it the other way around(which involves finding the right modules to load them manually launching the graphical environment)).
```
reboot
```

---

### Post by lordmonkeyu on 2009-09-22
Thanks for help but... don't know why i restarted and there I have - normal graphic desktop on which I am now writing :)

BTW how can I expand this partition used by ubuntu ? cuz I have now 30 MBs of space and can't download upgrades etc.

---

### Post by scragar on 2009-09-22
It's probably easier from the liveCD since Gparted doesn't come installed by default so installing it is out of the question.
Before you install it though launch the text editor like so:
```
gksu gedit /etc/fstab
```
And change the lines like so:
```
[color=red]#[/color]/dev/sda1
[color=red]UUID=3b3df30f-2262-447f-ac7b-d1472ec5ebbe[/color] /home ext4 defaults 0 2

[color=red]#[/color]/dev/sda2
[color=red]UUID=a28eabe1-9088-4e13-9d6f-6f082b79e17e[/color] / ext4 defaults 0 1
```To:```
/dev/sda1 /home ext4 defaults 0 2

/dev/sda2 / ext4 defaults 0 1
```So that resizing the partition doesn't cause errors in the partition identifiers that might cause errors.

On the live CD it either falls under system tools in the applications menu or under system>administration.

---

### Post by raymondh on 2009-09-22
> **lordmonkeyu said:**
> 

BTW how can I expand this partition used by ubuntu ? cuz I have now 30 MBs of space and can't download upgrades etc.

This is assuming windows and ubuntu root (/) reside BESIDE each other.  

*If unsure, access gparted (system > admininstration > partition editor), take a screenshot (applications > accessories) and saved and post back the screenshot.  If unable to make a screenshot, open a terminal and type (as well as post back)

```
sudo fdisk -l
```


1.  Back-up your files
2.  Defrag windows
3.  Use the windows disk management tool to shrink the windows partition to desired size and then quit/exit
4.  Boot into the liveCD and in live session (try ubuntu....), access gparted
5.  Ensure that partitions are UNMOUNTED.  (Just Rt. Clk and if given the option to unmount, do so.  For swap, select swapoff)
6.  Highlight Ubuntu root (/) and resize/enlarge
7.  Review and apply.

Oh, and welcome to the forums and Ubuntu.

---

