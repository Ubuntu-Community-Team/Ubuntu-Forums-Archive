---
title: "PDA, USB &amp; Fiesty"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by gjtoth on 2007-04-25
This has PROBABLY been beat to death somewhere but, any search I tried brought nil results.

I've installed (clean) Feisty (RC).  I've tried getting my Sony Clie' to synch up but haven't had any luck.  It used to synch up just fine in Edgy and during the beta Feisty (installed via upgrade... not a clean install).  lsusb produces:

Bus 009 Device 001: ID 0000:0000
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 002: ID 046d:c517 Logitech, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 006 Device 003: ID 04b8:0811 Seiko Epson Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 04cc:1521 Philips Semiconductors USB 2.0 Hub
Bus 004 Device 001: ID 0000:0000

which tells me it's not even being detected.

I've also tried the suggestion to run sudo modprobe visor and, if worked after that to add visor to /etc/modules.  No joy.  It didn't work.

I've tried 2 different cables/cradles and every usb port on this box (12 in all) and still ... no joy.

I've installed and uninstall gpilot, jpilot and kpilot... nada

Anyone got any suggestions/ideas?  I'm tapped out.

---

### Post by SonicSteve on 2007-04-28
I have a sony clie sj22 and I have the exact same trouble. The palmOS devices under preferences can't recognize it. I tried all the possible connection options.

---

### Post by SonicSteve on 2007-04-28
OK so I got it to work by typing this command in the terminal

sudo modprobe visor

and my device path was /dev/ttyUSB1

after running that command, and then using that device path palm os devices recognized my sony clie, then I tried syncing with Jpilot (and making device path change in Jpilot settings) it worked!!!

---

### Post by gjtoth on 2007-04-28
> **SonicSteve said:**
> OK so I got it to work by typing this command in the terminal

sudo modprobe visor

and my device path was /dev/ttyUSB1

after running that command, and then using that device path palm os devices recognized my sony clie, then I tried syncing with Jpilot (and making device path change in Jpilot settings) it worked!!!

I still have nada... :(

---

### Post by SonicSteve on 2007-04-28
BTY,
When I searched the forums I used these searches
Sony clie
Gnome Pilot
Between the 2 I found a few threads that helped me taking clues from each one. In the end I don't know if I found a work around or if the modprobe command will remain after a reboot, or if I need it after a reboot. That's step 2.

[B][COLOR="Red"]OK so after trying a few times I found that unless I run the command 
sudo modprobe visor

I can't hotsync my sony clie.[/COLOR][/B]

New update:
[COLOR="Blue"]**I have found that this work around is very inconsistent. I tried adding the visor kernel to the /etc/modules file but that had no effect. Though I may have done it wrong. I since removed it from the "modules " file and tried running the command from the terminal. I still haven't found the secret to why it sometimes works.**[/COLOR]

---

### Post by gjtoth on 2007-05-04
> **SonicSteve said:**
> BTY,
When I searched the forums I used these searches
Sony clie
Gnome Pilot
Between the 2 I found a few threads that helped me taking clues from each one. In the end I don't know if I found a work around or if the modprobe command will remain after a reboot, or if I need it after a reboot. That's step 2.

[B][COLOR="Red"]OK so after trying a few times I found that unless I run the command 
sudo modprobe visor

I can't hotsync my sony clie.[/COLOR][/B]

New update:
[COLOR="Blue"]**I have found that this work around is very inconsistent. I tried adding the visor kernel to the /etc/modules file but that had no effect. Though I may have done it wrong. I since removed it from the "modules " file and tried running the command from the terminal. I still haven't found the secret to why it sometimes works.**[/COLOR]

I'vd tried everything I can find on here and some things I googled for.  Nada... nuthin.... zip...

---

### Post by gjtoth on 2007-05-09
Bump... nudge... elbow

---

### Post by lazyart on 2007-05-13
If this is feisty, try "usb:" as the serial port/connection type.

---

### Post by gjtoth on 2007-05-13
> **lazyart said:**
> If this is feisty, try "usb:" as the serial port/connection type.


Thanks.  Tried it... still nada

---

### Post by gjtoth on 2007-05-13
After beating my head against the wall ](*,) I accidentally stumbled upon a Sony Clie troubleshooting guide.  Of course, all the obvious stuff was mentioned THEN, I noticed one of the steps was to do a soft reset.  Hmmmmmmm... sez I.  I do the soft reset (push in the reset button in the back) and attempt to synch.  VOILA!  We have lift off!

Hope this works for you, too!

---

### Post by forrestallen on 2008-04-27
This link helped me sync my Clie:
[http://ubuntuforums.org/showthread.php?t=3591&highlight=PalmOS]("http://ubuntuforums.org/showthread.php?t=3591&highlight=PalmOS")

The key was to press the Clie HotSync button BEFORE leaving the "Settings" page in the wizard.

---

