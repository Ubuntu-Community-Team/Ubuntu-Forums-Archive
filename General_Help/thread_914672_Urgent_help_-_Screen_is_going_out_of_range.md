---
title: "Urgent help - Screen is going out of range"
date: 2008-09-09
forum: General Help
---

### Post by chewit on 2008-09-09
Need Help!

I booted into Ubuntu this morning. The black and white screen appeared showing all the programs it is loading up. However, when Ubuntu switched to the login screen, my monitor said it was out of range. My resoultion must have messed up, but i can't change it cause i can't see anything.

I have tried rebooting into recovery mode and trying to fix the problem. I have tried reconfiguring xorg from recovery mode, but all it reconfigures is the keyboard then it stops reconfiguring xorg. I have tried editing xorg, but that didn't work. I also changed a thing in GRUB on the kernal option, by typing vga=773 (for example). 

So after all that, I thought I might just reinstall. So I loaded up a live CD of 8.04, loaded up all find until again it got the the graphic user interface. Again my screen said it was out of range. I tried 8.04, 7.10 & 6.06 live CDs. I get the same problem. Live CDs don't touch the hard drive, so if there is a problem with my Ubuntu install why does it effect the live CDs as well.

My specs are below. Also my screen is 15inch, it can accept up to 1280x768 75hz.

---

### Post by cdtech on 2008-09-09
Try this in recovery mode:
sudo dpkg-reconfigure xserver-xorg

---

### Post by chewit on 2008-09-09
Thats what I have done. It only configured my keyboard!

---

### Post by chewit on 2008-09-09
bump.

---

### Post by cdtech on 2008-09-09
> **chewit said:**
> Thats what I have done. It only configured my keyboard!

Add the -phigh flag:
sudo dpkg-reconfigure -phigh xserver-xorg

Is this from a new install or just happened? Be sure (if you can get to it) that the proprietary drivers are selected within the "System > Administrator > Software sources" then update.

---

### Post by chewit on 2008-09-10
Thanks, but I have fixed the problem now. If you just unplug the monitor then switch on your computer. Once its all booted up, plug it in and Ubuntu thinks it as a generic monitor. Problem solved.

Could anyone tell me where I can find or the name of the application in Ubuntu which allows you to change the gfx card driver, the screen your using and the screen resolution.

---

