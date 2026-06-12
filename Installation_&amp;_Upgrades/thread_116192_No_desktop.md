---
title: "No desktop"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by gladgrad on 2006-01-12
It's only taken me five days to get this far!

I initially had problems getiing the install disk to complete the installation.  Every time I tried it would stall at a different point within either the Base System install or the Copying extra packages to hard drive step.

I tried two differently sourced ISO images burnt to two different CDROMs but still random failures.  I've not done a md5 check on either ISO image.  When I finally did get what appeared to be a relatively complete system the reboot threw up a GRUB error which I traced down to the fact that my old BIOS was not capable of dealing with a large disk partition.

Start again - but this time manually select a small partition size.

After several more attempts the initial nstall process completed, rebooted successfully and began to install the extra packages.  98% through this process it stalled again.  It did reboot successfully an appear to begin to load with lots of OK signs.  I was able to login - but no desktop just a command line and $.  No supposedly wonderful Ubuntu desktop.

Help - I'm about to give up on Ubuntu.

I should add I've installed Fedora and SUSE on this machine previously with no problems.  Why is Ubuntu so difficult!

---

### Post by kaamos on 2006-01-12
when you are in the promp, try these:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop
```
and then
```
sudo dpkg-reconfigure xserver-xorg
```
When you have configured the video settings:
```
sudo /etc/init.d/gdm restart
```
Hope this helps!

---

### Post by gladgrad on 2006-01-13
Thanks for the advice - it worked.

I'm not sure I got everything right configuring the video, mouse and keyboard, but at least I've got a working system now and can reconfigure the keyboard etc. if needed.

---

