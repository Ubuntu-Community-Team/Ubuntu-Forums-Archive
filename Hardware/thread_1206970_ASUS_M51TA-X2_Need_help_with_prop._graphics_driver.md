---
title: "ASUS M51TA-X2: Need help with prop. graphics drivers"
date: 2009-07-07
forum: Hardware
---

### Post by jon_z on 2009-07-07
Good afternoon,

I have a ASUS M51TA-X2 laptop.  When windows was installed on the machine, the computer has two video cards.  The ATI Mobility Radeon HD 3650 kicks in while plugged in for advanced graphics, and a lower end card (ATI 3200) for powersaving.  I have attempted multiple times to get ATI catalyst 9.6 to work in jaunty 9.04 with no success.  

When booting up after installing fglrx, the screen goes black with red bars across the screen, and ubuntu is shown twice 3/4 at the top of the screen with the colors distorted.  

I have attached two screen captures of the screen as well as one of the badge of the computer.

```
lspci
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

```
By using ATI Tools i have determined that the 3650 has the device id of: 0x9591

Please let me know if anyone has had success properly getting this video card combo to work fully.  If you need any more information on my system, i will be glad to provide it.

Thank you,

Jon

*Edit*  I have tried compiling the ATI driver from amd.ati.com  no avail.
I have tried using the Envy/ng installer.  No avail.
I have tried using the GIT driver. No avail.

---

### Post by jon_z on 2009-07-08
Daily Bump

---

### Post by jon_z on 2009-07-11
Bump

---

### Post by jon_z on 2009-07-11
Does anyone have any idea how to downgrade the Xserver to a lower version that fglrx would work on?

---

### Post by jon_z on 2009-07-24
Does anyone know if this card combination is now supported with the ATI 9.7 Driver?

---

### Post by rmartinez79 on 2009-10-18
Hello jon_z, I have the same problem as you.
Just in case, my M51Ta has this two graphic cards:

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

I installed several versions of fglrx with Ubuntu but none of them worked. When I install Ubuntu 9.04 from scratch 2D acceleration was great, but no 3D. Lastly I tried radeonhd 1.3.0 and 2D works well but the computer doesn't turn off normally, I must press the button. I made some changes in xorg.conf to see if linux it could recognize the HD3650 card, so I specified the PCI of the card I wanted Ubuntu to recognice (PCI 2:0:0), but it didn't work. If I specify the integrated card (PCI 1:5:0) or nothing it works fine, but of course with no 3D...

In Phoronix forums I was told to install fglrx from Synaptic in Ubuntu 9.10 ([http://phoronix.com/forums/showthread.php?p=96103&posted=1#post96103](http://phoronix.com/forums/showthread.php?p=96103&posted=1#post96103)) so, this is what I did with no good results:
(1) Installed from scratch Ubuntu 9.10 beta 64bits (in other partitions Ubunut 9.04 64bits, Vista 32bits)
(2.0) Upgraded everything that could be updated (kernel 2.6.31-14,...)
(2.1) Restart
(3) Installed xorg-driver-fglrx (2:8.660-0ubuntu4) and all other dependencies which were needed from Synaptic
(4.0) In terminal: "sudo aticonfig --initial -f"
(4.1) A xorg.conf file was created (before there was no xorg.conf) with the following text:

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

(4.2) Restart... XORG CRASHED!
(5) I tried changing in xorg.conf BusID to "PCI:2:0:0" but it always crashes...
(6) Finally I changed the name of xorg.conf so that it doesn't read it and now it works but, of course, no 3D acceleration
PLEASE HELP!

Shoul I install the fglrx manually?? following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by rmartinez79 on 2010-02-15
In this post it is detailed how to install switchable graphics under Linux (Fedora12):
[http://phoronix.com/forums/showthread.php?t=21979](http://phoronix.com/forums/showthread.php?t=21979)
Still work to do, but very promising situation and good 3D acceleration.

---

### Post by rmartinez79 on 2010-05-07
Update!
If you want to use hybrid graphics on linux follow this HowTo [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) and post your experience at the mailing list [EMAIL="hybrid-graphics-linux@lists.launchpad.net"]hybrid-graphics-linux@lists.launchpad.net[/EMAIL] of [https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")
Best and enjoy your hybrid graphics on linux!
rm

---

