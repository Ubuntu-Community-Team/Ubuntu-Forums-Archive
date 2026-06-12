---
title: "Brother MFC-8500 scanner stopped working randomly"
date: 2013-01-16
forum: Hardware
---

### Post by pops66 on 2013-01-16
I have two scanners attached to my computer, a Brother MFC-8500 and an HP Photosmart C4210.  I was using gscan2pdf with the HP and accidentally set it to scan "all" pages instead of just one from the flatbed.  A known issue caused the scanner to continuously scan with no way of stopping it.  I turned off the scanner, saved the document and the tried scanning a different document with the Brother scanner.  Instead of the normal operation I usually get, I instead got "Unable to open device, Invalid Argument"

scanimage -L gives me:
```
WARNING: gnome-keyring:: couldn't connect to: /run/user/**********/pkcs11: No such file or directory
device `brother:bus4;dev1' is a Brother MFC-8500 USB scanner
device `hpaio:/usb/Photosmart_C4200_series?serial=CN7ACNF046055B' is a Hewlett-Packard Photosmart_C4200_series all-in-one

```

this does not seem to align with lsusb:
```
Bus 001 Device 011: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 0bc2:5071 Seagate RSS LLC 
Bus 004 Device 002: ID 2040:4903 Hauppauge HS PVR
Bus 004 Device 004: ID 04f9:0113 Brother Industries, Ltd MFC-8500
Bus 006 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 006 Device 003: ID 046e:5542 Behavior Tech. Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 046d:c21d Logitech, Inc. F310 Gamepad [XInput Mode]
Bus 001 Device 013: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 014: ID 0c45:6340 Microdia 
Bus 001 Device 015: ID 03f0:5c11 Hewlett-Packard PhotoSmart C4200 Printer series
Bus 001 Device 016: ID 04e6:5116 SCM Microsystems, Inc. SCR331-LC1 / SCR3310 SmartCard Reader

```

uname -r
```
3.5.0-17-generic
```

lsb_release -a
```
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 12.10
Release:        12.10
Codename:       quantal

```

dpkg -l brscan
```
ii  brscan         0.2.4        amd64        Brother CUPS Printer Definitions

```

hours of searching have given lots of helpful suggestions including modifying /lib/udev/rules.d/40-libsane.rules and adding
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

```

also copying brscandec, brcolm, and sane  libraries from /usr/lib64 to /usr/lib.  I had to do all thisto get it working the first time and that hasn't changed.

I uninstalled and re-installed sane and the brscan packages.  I checked the Brother [[COLOR="Blue"]website[/COLOR]]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") for help.  I also have done the obvious and rebooted.

So far nothing has managed to solve my problem, which has made a scanner that has been working great act like there is something wrong that it cant work.  Any help would be appreciated. :)

---

### Post by pops66 on 2013-01-19
Bump?

---

### Post by pops66 on 2013-01-26
Anybody?

---

### Post by Imagineer66 on 2013-04-16
I get the same error.  Everything was working fine for a month and now the same error.  Mine gives an error in gnome-keyring with the data file in the tmp directory.  I'm thinking a security key was stored there and, as should be expected, the tmp directory got cleaned out.

Mark

---

### Post by Imagineer66 on 2013-04-17
A bit more after a couple of days of searching.  Following a hunch, I  bet that the problem wasn't with the scanner or scanner software at  all.  I chased gnome-keyring down its rabbit hole.   

 Here's the  upshot.  When you login the gnome-keyring server copies the encryption  keys for software you have access to somewhere in a session file for  you.  Then any software uses the lib to check that key.  Guessing  somewhere in Brother's software they check their key.  The hiccup comes  if somehow the chain (notice I didn't say path) to that key gets lost or  broken.  In my case, I'm running Linux Mint which instead of using  gnome-keyring-*  uses mate-keyring-*.  Normally, this wouldn't be a  problem, and it wasn't when I installed the scanner.  Because the  Brother software installed in to the Mate keyring.  What broke things  for me is when I installed another piece of gnome software which instead  of using mate-keyring, goes back to using gnome-keyring.  So, it  installed gnome-keyring* which then claimed to be the default keyring  manager.  But, since it was just installed it had no idea about the rest  of my Linux Mint system and badaboom, badabang things started  breaking.  Soooo.....  How to fix?  I'm not sure of a the permanent fix  but I found a workaround, at least for me.  

Look in 
/etc/xdg/autostart/   

you  will find a bunch of gnome-keyring-* files.  You may also find  mate-keyring-* files or other somesuch as xfce-keyring-*, etc.  In each  of these files (gnome-) there is a line, 

OnlyShowIn=GNOME;Unity;  {there may be others}

This tells gnome-keyring when to start a local keyring copy.  My solution was to add the other environments.

OnlyShowIn=GNOME;Unity;MATE;LXDE;XFCE

I  then rebooted my machine.  Don't know if a reboot was exactly required  but since this was such a low-level thing and I had already spent days  tackling this problem, I went with the complete option.  Now, I have  both mate-keyring* and gnome-keyring running concurrently.  Since they  both share the same base keyring files, they seem to work ok; just each  serving to the whichever program asks for them personally.


This may or may not fix your problem, but I hope it gives you a vector to search.

Hope this helps,
Mark

---

### Post by kurt18947 on 2013-04-17
Impressive detective work.  I've had good luck with Brother all-in-ones and this is something I'll keep in mind.  Good job.

---

