---
title: "Ubuntu hangs on startup :("
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by Strev_123 on 2006-01-30
Hi all, downloaded ubuntu last night, installed on a 5gb partition (created using the partitioner included at the installation), Windows ME resides on the other 20gb partition along with a SWAP partition. I have all the latest drivers and BIOS for my system. Installation went without a hitch, all hardware detected etc... The problem occurs when I select Ubuntu from the boot menu, prestart checks(??) all say "ok" and the bar goes all the way to the right. Then I get a blinking white line at the top left of a blank screen, then HDD activity stops and line stops blinking, nothing else happens. System is quite old, but easily meets min spec for Ubuntu; just can't see where the problem is.

System specs are (if they help);
PIII 766EB, 128mb RAM, Gigabyte MB 810i chipset, TNT2 (latest drivers),
25GB Quantum Fireball HDD, Samsung CDRom and Liteon CDR drives.

---

### Post by sprok8 on 2006-01-30
Have you checked your first virtual console for verbose output? Click Ctrl-Alt-F1 to see how far the boot process went...

---

### Post by Strev_123 on 2006-01-30
Sorry don't know how (what's a virtual console??), you're talkng to a complete stranger to linux, can someone tell me how step by step please.

---

### Post by ububaba on 2006-01-30
After the start login I'm told that I cannot proceed any further because for accessing the folder '/home', I need different rights. How is that possible? Totally crazy.

---

### Post by sprok8 on 2006-01-30
Linux can actually support many users at once. To see this feature in action, you can use virtual consoles by holding Ctrl and Alt down and pressing F1, F2, etc.

In Ubuntu the first console (Ctrl-Alt-F1) displays verbose output detailing what happened during the boot process. The graphical display is on Ctrl-Alt-F7 by default.

You can log in as yourself or a different user on any of the other consoles F2 to F6. This comes in useful if something goes wrong with the graphical display for example.

---

### Post by Strev_123 on 2006-01-30
Err.. I dont think that will help... all I see is a blank screen with a single white line at the top... no key presses do anything and no HDD activity. I suppose this is right before Ubuntu loads the desktop, except it doesn't...

---

### Post by dude of wonders on 2006-01-30
yay i'm not the only one same problem here man it just freezes with the white underscore in the top left corner, i'm so close to having it installed, and yet stuck here. (about ready to give up.)[-(

---

### Post by Strev_123 on 2006-01-30
Just been told in IRC it could be a driver or Xorg issue... Trying to install drivers off liveCD (once it's downloaded - 1hr 19mins and counting), keep you informed of any progress D.O.W.

---

### Post by dude of wonders on 2006-01-30
i dont know its looking grim. i'm going to try one more time and then i give up. i bet its probably something really simple to, sucks though cant spend forever on trying to get it installed though.:-k

---

### Post by dude of wonders on 2006-01-31
yes i'm happy to say i finally have unbuntu installed :D \\:D/ :cool:  i don't know if this will solve your problem, but i took out my graphics card and let it run off the motherboards built in chip, and reinstalled and it ran perfectly, i'm typing to this right now using the ubuntu. you might not have to reinstall the program removing the graphics card alone might be enough ,but i jumped the gun and reinstalled hope this helps man.

---

### Post by Strev_123 on 2006-01-31
YAY... pulled out nvidia card, reinstalled old intel 82810 chipset under windows and bam!! no need to reinstall either... now typing this from ubuntu... now about those nvidia drivers.... :D

---

### Post by oxman on 2006-01-31
I have just built a monster 64 bit AMD box for an acquaintance. 2GHz of ram and a 7800 nvidia card. I've been suggesting he use linux for some time. I use Fedora Core but suggested he use ubuntu. After the install I get a brown screen and mouse cursor. It hangs right there. No logon screen.
So take out the nvidia card. reboot and then what?

Any help is appreciated.

---

### Post by jimsmith80220 on 2006-01-31
I had the same problem with TNT which is on the legacy list with instructions to fix it at
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

### Post by oxman on 2006-02-01
I've had to install proprietary nvidia drivers for my FC3 and FC4 installs so it shouldn't be too much different BUT that thread is a monster :) It looks like it had almost 850 posts! Thanks for the heads up!

---

### Post by LOBIWAN on 2006-02-02
Thank God I've Found You, Someone With Exactly The Same Problem.
Pentium Iii, New Hd, 128 Mb Ram And Just A Frozen Cursor To Look At. Is There Any Hope

---

### Post by oxman on 2006-02-02
The most likely scenario is problems with your xserver and or video card. One of the areas of "conflict" between free and open source software and proprietary and closed source software is in the arena of hardware/software interfaces. 
If it is a hardware/xserver problem you will have to boot with run level 3 and edit your /etc/X11/xorg.conf and/or possibly mess with kernel modules. It sounds scary but do not fear. Take your time and do your homework by searching the net for answers. Punch in your symptoms and operating system on google and on this site for answers. The thread that I was directed to above is very informative:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

