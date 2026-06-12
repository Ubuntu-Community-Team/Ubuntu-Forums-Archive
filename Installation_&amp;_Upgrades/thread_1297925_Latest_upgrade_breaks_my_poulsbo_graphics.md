---
title: "Latest upgrade breaks my poulsbo graphics"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Lifer999 on 2009-10-22
Today's kernel upgrade (2.6.28-16-generic) broke my Intel graphics on my Dell Mini 12. I'm unable to get a graphical log-in screen and am offered low-res graphics after log-in.

Usually I issue the command:

[FONT="Courier New"]**sudo apt-get install psb-kernel-source**[/FONT]

One re-compilation and reboot later I'm good to go.  Not this time.  

As of now I'm simply booting into the previous kernel so there's no crisis. Should I wait for 9.10?

I've not triaged a problem like this before and don't know what info is needed so all guidance is appreciated.

---

### Post by FallinWithStyle on 2009-10-22
I appear to be having graphics-related issues as well, although mine don't appear to be as severe (I have a Dell mini 10v). After logging in, my laptop screen periodically (every 1-2 minutes) distorts for a split-second. I actually installed several updates:

Commit Log for Thu Oct 22 20:39:52 2009

Upgraded the following packages:
libpoppler-glib4 (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.5
libpoppler4 (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.5
linux-generic (2.6.28.15.20) to 2.6.28.16.21
linux-headers-generic (2.6.28.15.20) to 2.6.28.16.21
linux-image-generic (2.6.28.15.20) to 2.6.28.16.21
linux-libc-dev (2.6.28-15.52) to 2.6.28-16.55
linux-restricted-modules-common (2.6.28-15.20) to 2.6.28-16.21
linux-restricted-modules-generic (2.6.28.15.20) to 2.6.28.16.21
poppler-utils (0.10.5-1ubuntu2.2) to 0.10.5-1ubuntu2.5
tzdata (2009n-0ubuntu0.9.04.1) to 2009o+repack-0ubuntu0.9.04
xserver-xorg-video-intel (2:2.6.3-0ubuntu9.3) to 2:2.9.0-1ubuntu2~xup~3

Installed the following packages:
linux-headers-2.6.28-16 (2.6.28-16.55)
linux-headers-2.6.28-16-generic (2.6.28-16.55)
linux-image-2.6.28-16-generic (2.6.28-16.55)
linux-restricted-modules-2.6.28-16-generic (2.6.28-16.21)

What is the procedure to boot with the previous kernel? Do I need to modify GRUB in some way?

---

### Post by dodtsair on 2009-10-23
I am having graphical problems after the last update as well.  Instead for me it is a full lock out.  The Ubuntu loading screen is displayed with the wrong colors very small and tiled along the top row of the monitor.  

Key board does not work, mouse does not work.  Shutting down gdm does not give me a text login.  Right now I can only access the system via ssh.

Rolling back to previous kernels does not help me.

---

### Post by Lifer999 on 2009-10-23
> **FallinWithStyle said:**
> 
What is the procedure to boot with the previous kernel? Do I need to modify GRUB in some way?

Well, you could access the grub menu (by pressing ESC) upon boot up but is a pain. I edited the grub menu file.


Assuming you've not purged your system of previous kernels, open a terminal and give the command:

**sudo gedit /boot/grub/menu.lst**

Change the **default** setting to the kernel you'd like to boot into (they will be listed in order further on in this file).  Note that 0 is the first kernal, 1 is the second, etc....

This old kernel has a number of security holes, so for me this solution is temporary (just until 9.10 comes out).

HTH.

---

### Post by FallinWithStyle on 2009-10-23
Thanks Lifer999, I tried a couple older versions of the kernel-- I still had the same issue. I finally reverted:

xserver-xorg-video-intel (2:2.6.3-0ubuntu9.3) to 2:2.9.0-1ubuntu2~xup~3

My system has been up for about 15 minutes with no issues (I'm back on the 16 kernel now).

---

### Post by sandeep.manne on 2009-10-24
Mine too broken please let me know if there is any update. I am using dell mini 10

---

### Post by satbunny on 2009-10-24
Try this, remove the old and then install the new. Worked for me.
> 
sudo apt-get remove psb-kernel-source
sudo apt-get install psb-kernel-source

---

