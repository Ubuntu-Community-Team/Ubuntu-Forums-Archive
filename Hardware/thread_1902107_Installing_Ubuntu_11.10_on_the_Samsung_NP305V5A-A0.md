---
title: "Installing Ubuntu 11.10 on the Samsung NP305V5A-A04US laptop"
date: 2011-12-30
forum: Hardware
---

### Post by ahmrahtcheer on 2011-12-30
This Samsung Series 3 computer is a new (released within the past few months) mid-range model that comes with with Windows7 installed.  Many of the chipsets apparently are relatively new, specifically the ATI Radeon 6620g graphics and an Atheros AR9485 wireless network controller.  I initially tried to install Ubuntu 11.10, then tried several other distros, and was only able to solve the video and wlan issues with Ubuntu.  Here's what I ran into:

Problem:  During bootup of the LiveCD, the screen would display graphics for a short period, then a prompt in the upper left corner, then it would go dead.  Not blank, but dead.

Solution:  as soon as the first graphical screen appeared, I hit F6.  This brought up the Boot Menu.  Selecting F6 again allowed me to add parameters to the bootup, and I selected nomodeset.  Hitting escape allowed me to select how I wanted to boot (run as livecd, install, etc.) and I selected install.

Once installed, I booted into Ubuntu and experienced the same issue.  Rebooting and selecting recovery mode in GRUB allowed me to boot to command line.  There, I tried to start the GUI via startx, but it encountered a fatal error and exited back to the command line.  Typing "nano /var/log/Xorg.0.log" called up the error log file and showed me the problem:  the fglrx module was missing.  sudo apt-get install fglrx solved that issue and I was able to go into GUI with startx.  After rebooting, GDM appeared--problem solved.  Now I have accelerated 3D graphics, equal to, or better than those in Win7 on the same computer.

Problem:  Linux was not recognizing either my wireless or wired network controller.

Solution:  Research on Google indicated that the problem lay with earlier kernels, that kernel 2.6.39 and later had no problems with this wireless controller.  I've not yet attempted to connect via the Realtek RTL8111/8168B wired network controller, so can't answer to whether or not it has similar issues.  The solution lay in selecting a distro with a later kernel.  As hoped, Ubuntu found my wireless controller and allowed me to connect to the internet via my wireless router during installation.


So, now I have Ubuntu 11.10 on my new Samsung.  This is not my first experience with Ubuntu.  I've been using it steadily since v7.x, and it's installed on the other three computers in the house--as sole OS on one.  However, my initial attempt to install it, having the screen go dead, caused me to look elsewhere.  Foolish of me, as it turns out, Ubuntu's the one distro for which I could find or figure out the answers to my problems.

---

### Post by rajeeja on 2012-01-03
Just bought this: Samsung Series 3 NP300V4A-A03US 14-Inch Laptop from Amazon
i5 with intel integrated graphics card, do you recommend installing Ubuntu, I wanted to go with 10.04, but it seems from your post that this would need newer kernals?

---

### Post by ms0chez on 2012-03-10
Appreciate this. Bought this same model and it was a pain trying to figure out to get Ubuntu to work (new to Ubuntu). Was wondering though, if you got the touch pad to wok properly without having to use terminal every boot to fix it?

---

