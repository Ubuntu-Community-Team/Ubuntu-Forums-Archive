---
title: "2nd Hard Drive Installation Screwup"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Mortus on 2009-03-20
Ok, just because for the sake of everything, I must say the whole story.

I took a hard drive from another computer, made it a slave, and added it to my current desktop.

I also had to set the first hard drive to master.

I could boot into windows, edit the hard drive, all that good stuff.

I booted from Ubuntu ( 8.10? ) Live CD to install to my second hard drive.

I chose the correct hard drive to format and such ( i checked multiple times ) and installed.

I left the room, let it install.

I came back to it after a little while, it was a plain black screen with no system sounds or anything, so I shut it down.

I try to turn it on, it cannot load windows or ubuntu.  ( GRUB Error 21 ).  When i load from CD, it loads up the live CD again, and it shows that my first hard drive is still intact, and the second hard drive has a linux installation.

I don't know how to fix the boot menu, nor do I know how to fix the Linux Installation.

I am currently using my bro's computer, please help.

---

### Post by taurus on 2009-03-20
Try booting from Ubuntu LiveCD again and see if you can reinstall GRUB to MBR this time.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mortus on 2009-03-20
Ok, I tried that.  It says to type in "find grub/stage=1" then a bunch of other directions.  All it told me was "file not found" and there were no other directions to help me with that error.

Should I try SuperGrub?

---

### Post by taurus on 2009-03-20
Sounds like it's never got a chance to install GRUB; therefore you don't have /boot/grub directory.  Can you boot Ubuntu from the harddrive with the LiveCD?  There is an option on the LiveCD that allows you to boot Ubuntu on the harddrive.  If you can boot with that option, then you should consider installing GRUB with synaptic or add/remove.

---

### Post by Mortus on 2009-03-20
I went into the live cd menu and hit "Boot from First Hard Disk" if that is what you are referring too.  It had the same error.  I am just going to reinstall ubuntu in entirety onto the hard drive, I need to sleep, I have work in 7 hours.  If it doesn't work in the morning, I will report back in.

---

### Post by Mortus on 2009-03-20
I don't know if I should have edited my previous post or not, but here goes.

I got it to boot into windows.  When I reinstalled ubuntu, it gave me the black screen.  I hit the keyboard, and it asked me to restart.  I did that, got the same error.  I used supergrub to get it to boot into windows at startup.  I am going to get a new ubuntu disk and see what happens.

Wish me luck!'

------

Ok, I managed to get my original boot, and reformatted the ubuntu hard drive.  I am installing it wubi, I don't know what the problem was today, I did use a fresh disk.  I would like to eventually use the hard drive for ubuntu, but not tonight... I have 5 hours to sleep before work.

Thank you for helping!

---

### Post by Mortus on 2009-03-21
I managed to install ubuntu on the second hard drive.  I just switched the master/slave config.   Thanks for your help Taurus!

---

