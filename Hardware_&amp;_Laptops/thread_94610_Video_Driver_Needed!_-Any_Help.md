---
title: "Video Driver Needed! -Any Help?"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by toadhall on 2005-11-24
Hi all,

I have a laptop (Sager 5100c - NP5120/5130) with which I am trying to run Ubuntu 5.10 Breezy. The video card is correctly detected as an S3 ViRGE/MX chipset. However, I cannot set the resolution above 640X480. The screen is either an LG LP121S2 12.1" TFT SVGA or a Sanyo 12.1" HPA SVGA. The video chipset is S3 86C280-DB.

This is my first time loading Ubuntu (any release) onto a laptop. Up to this point, all installations have gone smoothly with all hardware detected correctly. Anyone have any thoughts?

I would really like to get Ubuntu working on my laptop instead of having to reinstall WinBlows... I am gradually trying to switch all my operating systems to various flavors of Linux.  I even have a Windows PDC using Samba to tie it all together at the moment, but it is a clunky solution to one that could really be elegant with just Linux and OpenBSD.  Any help is appreciated.

---

### Post by toadhall on 2005-12-08
I managed to get the problem resolved. Reconfiguring XFree86 (xorg.conf) through dpkg reconfigure did not work; however, I did resolve the LCD display problem through a manual edit of xorg.conf. While the problem is not resolved 100% (the login screen needs to be adjusted), I did get X and GNOME to recognize the different resolutions. I set the default to 16 rather than 24 (as 24 is an unsupported setting on my monitor), and I added the vert refresh rate and horiz sync lines. I also eliminated the low res "640X480" resolution in all modes, which in retrospect was probably unnecessary.

Copy of xorg.conf follows with comments on what was removed and added:

Section "Device"
 Identifier "S3 Inc. ViRGE/MX"
 Driver "s3virge"
 BusID "PCI:1:1:0"
EndSection

Section "Monitor"
### Changed for clarity## Identifier "Generic Monitor"
 Identifier "LCD Monitor"
###### Remove these lines if you have trouble
 HorizSync 30-67
 VertRefresh 50-70
##### End of input ###
 Option "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "S3 Inc. ViRGE/MX"
# Monitor "Generic Monitor"
 Monitor "LCD Monitor"
 DefaultDepth 16
# DefaultDepth 24
# Edited Display Modes to eliminate low res
 SubSection "Display"
  Depth 1
  Modes "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth 4
  Modes "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth 8
  Modes "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth 15
  Modes "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1024x768" "800x600"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1024x768" "800x600"
 EndSubSection
EndSection

---

### Post by pseud0nym on 2006-03-29
All these sugestions seem to assume you have an xorg.conf.  None has been created and when X -configure is run, it dies with "Missing Output Driver" before creating an xorg.conf in /root.

i am using a ViRGE/MX card on a Toshiba 490CDT

---

### Post by Mach1US on 2006-08-02
I have same problem ,my resolution is 640x40 on toshiba 2180 with same video hardware(ViRGE/MX), ubuntu has recognised this card shoving it in device manager .
do i need a driver and if i do whe can i find it=D>

---

### Post by toadhall on 2006-08-03
>>do i need a driver :-k 

Ubuntu should have loaded the driver during install.  It was a matter of adjusting the screen resolutions in xorg.conf to get my laptop so I could see anything.  I had to force the screen resolution to 800X600 and leave it, as I could not get it to do any better with the resolution (limitations of the display on my particular laptop).  Also set the default depth to 16, if you are having trouble.

Open a terminal window and type in #dpkg-reconfigure xserver-xorg

This will walk you through the steps to get the display configured correctly.  If you cannot get it to work, you will have to edit xorg.conf located in /etc/X11/xorg.conf with the configuration located in the previous post.  I was just learning Linux when I installed it on that laptop, and it was a pain in the butt to do this.  ](*,) The nice part is that the Ubuntu install is still stable on my laptop, and I use it all the time.

---

