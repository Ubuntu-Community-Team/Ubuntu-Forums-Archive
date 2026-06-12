---
title: "X server will not start on boot"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by dconklin on 2005-12-03
HP ZV6100 (2Gh AMD-64) with ATI Mobility Radeon Express x200 video board with 128M VRAM. Installed Ubuntu 5.1 and on reboot, after the splash screen and command line scrolling by, when the login: is displayed, instead of starting X and switching from cmd line to GUI, the X server failed to login warning appears. Looking at the info screen does not show anything wrong I can see. Any ideas?  thanks...

---

### Post by yaw on 2005-12-03
Hi

I also have the same problem....my notebk is hp zv6147...how do i solve...'failed to start x server' problem...

just installed ubuntu breezy..

yaw

---

### Post by Georgie-o on 2005-12-03
I purchased a new laptop - WinBook - AMD Sempron with an ATI Radeon Xpress 200M.  During the install I got a screen that said 

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the the X server output to diagnose the problem?"

and asks "Yes"  or "No"

 and it would not install.  How can I configure something if it won't even install?  Any help?  I use Ubuntu on my Desktop PC and really want to use it on my laptop.

p.s. Is this a Bug we should send to Ubuntu?  Will using KDE make a difference re: ATI use?

---

### Post by Lambert on 2005-12-03
I'm not that knowledgeable here but it sounds like it's using the wrong driver. 

Hit ctrl+alt+1 to get to a terminal; login then run this command

sudo dpkg-reconfigure xserver-xorg

Choose the vesa driver then try to login. If it doesn't give you all the correct options you may need to add a -phigh after reconfigure. Most default answers are ok when going through this. Just make sure you choose the vesa driver.

vesa driver is a generic driver which should get you going graphical. You will want to search and find the correct driver for your card though and install that later. There's a howto floating around here in the forums somewhere. Look under tips and tricks.

If you can't install then you need to add a boot parameter before starting something like vga=779 or driver=vesa etc... hit F1 for help and look for the section on adding boot parameters etc... Then same thiing, after install you'll need to find what driver is correct and then look for howto on installing that driver.

---

### Post by Georgie-o on 2005-12-03
I've tried everything.  No luck.  I'm stuck with Windows unless Ubuntu can make a live CD that works with an ADM/ATI WinBook laptop.  I couldn't get anything to work after all of my attempts at Live/installs and I almost got stuck with a laptop that wouldn't even boot from the CD.  If a live distro works then maybe I'll be brave enough to try installing Ubunut on my laptop.  Really disappointing considering I wanted the laptop to work with, and learn linux.  Does anyone have any linux suggestions for a live CD that is VERY laptop friendly?

Thanks

---

### Post by dconklin on 2005-12-04
In order to run the sudo command, Ubuntu requires a root login and password, however, as this is the initial boot of Ubuntu, root hasn't been created (unless I reinstall and name the first user root, I suppose). So I can not now run the suggested sudo command to get the VESA driver loaded. Any ideas?

thanks

---

### Post by dconklin on 2005-12-04
well, ubunut is too clever to let me create a root user account on installation

oh well...

---

### Post by amp_man on 2005-12-04
sudo uses your *user* password, not the root one, or else you can use, i believe, 

```
sudo passwd root
```

to create a root password, first you will need to put in your user password, then the new root password twice

back on the subject, I'm having the same problem, with an HP ze2308wm, which is a Sempron 2800+ with the same ATI 200M chipset, also with 128mb of shared video memory (768mb total), and also running Breezy. I got it up and running once using the instructions [here](http://ubuntuforums.org/showthread.php?t=78269), but 3d rendering was still done by mesa, and after rebooting it went back to crashing X.

My first indication of a problem is at boot, I get the following lines:
> [4294669.063000] BIOS bug, local APIC #0 not detected!...
Loading, please wait...
insmod: can't read '/lib/modules/2.6.12-10-k7/initrd/vesafb.ko' : No such file or directory

Then, it goes through the normal boot sequence, and finally X crashes at startup. I've attached my xorg.conf and Xorg.0.log (being the crash log), they're both in xorg.zip. I realize this probably borders on thread jacking, but hopefully this problem is all along the same lines, as it all lies with AMD-based hp notebooks with the ATI Radeon Mobility 200M GPU. I hope someone can find a solution to this!

---

### Post by infinito on 2005-12-04
Take a look at this bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17421](http://bugzilla.ubuntu.com/show_bug.cgi?id=17421)
There's a modified .deb that works for me...

---

### Post by amp_man on 2005-12-04
I feel like an idiot, I got it running no more than a few seconds before you posted that, all I needed to do was dpkg-reconfigure xserver-xorg, either with or without that modified file, I can get into X just fine, and glxinfo reports the radeon as the opengl renderer. The only problem left, for me at least, is the missing vesafb.ko, which is really more of an annoyance than anything else (as this means it has to do a text-mode boot instead of the nice splash screen)

---

