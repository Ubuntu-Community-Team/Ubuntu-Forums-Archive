---
title: "Dual video card problems"
date: 2010-03-09
forum: Hardware
---

### Post by zeck28666 on 2010-03-09
Hi guys, im a linux newbie, i need a litle help.Im vj aand a sound enginer and we has a event in this weeken d and i need some special apps.

what i need to make:

(video mixer with svid out)->(PC with Pinnacale tuner and 2 video cards)-> 2 vga out for the projectors.

I has this videocards:
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a)

(and a Club3D delta chrome but it vorks with only vesa driver)

All hardwares working alone but when i put the ATI & nVidia to the computer working only one (absolute randomly witch one) OR works both in low resolution (640*480 56 Hz)
How can i setup to work the both cards in normal mode?

---

### Post by zeck28666 on 2010-03-09
Ps: sorry for my bad english :-s

---

### Post by Fafler on 2010-03-09
Would it be possible for you to find two more similar cards? Or maybe single card with two outputs?

I've been messing with setups like yours in the past, and it's always easier if theres only one driver and one video BIOS in the mix.

---

### Post by zeck28666 on 2010-03-09
I need only for this time and i has a lot of usles hardware junk and i dont want more :DFirst i try the Club3D what has dual outputs but it dont works...

i find a local pc store who sell used cheap cards but i dont find in hes list a linux compatibile card, you can?

[this is the list]("http://pcbonto.hu/portal/Budapest/PC_cuccok/Videobigyulak_4ee40ab971fb990c_0c4d9ac81571c7a3_.html")
(i try to deal with the seller for one time rent :D)

---

### Post by Fafler on 2010-03-09
The MGA450 would be a sure bet. [http://pcbonto.hu/portal/Budapest/PC_cuccok/Videobigyulak/AGP_foglalat/16MB_Matrox_G450_dualhead_AGP_VGA_kartya_4ee40ab971fb990c_439098_882315.html](http://pcbonto.hu/portal/Budapest/PC_cuccok/Videobigyulak/AGP_foglalat/16MB_Matrox_G450_dualhead_AGP_VGA_kartya_4ee40ab971fb990c_439098_882315.html)

So this is basically just a setup to convert the S-VIDEO signal to VGA?

---

### Post by zeck28666 on 2010-03-09
No its basicly extend a normal 4:3 picture to dual 4:3 ;) Ok, i go to buy this card and then try it. I hope it work. Thnx for the help!

---

### Post by zeck28666 on 2010-03-09
Here agin, i buy the card, (It works i see two monitors with same picture) download the driver from the matrox site and got this:

> [: 43: ==: unexpected operator
/home/bpm/matrox_driver-x86_32-4.4.0/install.sh: 57: function: not found
/home/bpm/matrox_driver-x86_32-4.4.0/install.sh: 69: function: not found
/home/bpm/matrox_driver-x86_32-4.4.0/install.sh: 78: function: not found
/home/bpm/matrox_driver-x86_32-4.4.0/install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6
/usr/X11R6
/home/bpm/matrox_driver-x86_32-4.4.0/install.sh: 141: function: not found
test: 178: 0: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
[: 178: ==: unexpected operator
-e \E[31mERROR: The X server drivers included in this installation package
-e        do not support the current version of your X server.

then i try the open version an got this:

> ~$ sudo sh /home/bpm/Munkaasztal/matroxdriver_mga-x86_32-4.4.4-installer.run --overwrite
Please, enter the directory to extract the files [/home/bpm/] mat
Creating directory mat/matroxdriver_mga-x86_32-4.4.4
Verifying archive integrity... All good.
Uncompressing Unofficial Matrox G-Series Driver by tuxx-home.at..............................................


========================================
   Matrox Linux Driver Install Script   
========================================

Can't find the X Server version you are currently running (1.4.0.90) in
this installers database, so for your convenience, I'll try to install
the latest available version (7.1.0) onto your system.

If you think this is alright, simply hit <RETURN> here, if you don't,
stop here by pressing CTRL-C and please post this notice in the
Unofficial Matrox Technical Support Forum ([http://matrox.tuxx-home.at](http://matrox.tuxx-home.at))
and I'll see what I can do for you.

Please strike any key to continue...
Overwrite option enabled.
  Do you wish to continue? (y/n) y

You are about to install the X server driver,
do you wish to continue? (y/n) y

Creating a new X server driver backup file
mga_drv.so.mgabak in /usr/share/matrox.

Renaming current X server driver backup file
mga_drv.so.100309201707 in /usr/share/matrox.

Backing up current X server HAL driver to backup file 
mga_hal_drv.so.mgabak in /usr/share/matrox.

Installing X driver...

Installing HAL driver...


I thin its ok, but whats next step?

i try reconfig the xorg with command 
> sudo dpkg-reconfigure xserver-xorg


but its only asking form my keboard...

---

### Post by zeck28666 on 2010-03-10
up! Pls help me guys! I think im in finish, dont constrain me to use windows...

---

### Post by Fafler on 2010-03-10
I'm 99% sure i did dual-head with xinerama on a G450 with the open source mga driver before i moved from AGP to PCIe and had to accept the change to nvidia binary drivers. I don't have time for a long post now, but try google.com/search?q=mga+xinerama

---

