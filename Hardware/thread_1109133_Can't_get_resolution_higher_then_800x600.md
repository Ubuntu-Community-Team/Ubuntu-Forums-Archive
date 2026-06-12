---
title: "Can't get resolution higher then 800x600"
date: 2009-03-28
forum: Hardware
---

### Post by DemiAlbedo on 2009-03-28
I just finished installed kubuntu 8.10 KDE 4 and everything went fine, so I thought.

Once the system boots up there is about 2" of black around my desktop, which shows a problem right there, however it gets worse. I tried looking under Settings >> System Settings and KrandrTray and it will not allow me to put the resolution higher then 800x600.

Checked Restricted drivers and there is nothing there.

When I do lspci I can see it shows my video card. VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82). I did a search for xserver-xorg-video-trident and I do have the driver installed.

Here is /etc/X11/xorg.conf file

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

As you can see the xorg file has some serious problems, because its not showing anything. 

I already tried running dpkg-reconfigure xserver-xorg and tried booting into the recovery and doing fix x server function and still nothing.

This is just frustrating so hopefully someone can help.

Thanks

---

### Post by alt236 on 2009-06-02
Try changing it to the following:

> Section "Device" 
  Identifier "Trident Microsystems CyberBlade XPAi1" 
  Driver "trident" 
  BusID "PCI:1:0:0" 
EndSection 

Section "Monitor" 
  Identifier "Configured Monitor" 
  Option "DPMS" "true" 
  HorizSync 30.0-60.0 
  VertRefresh 50.0-70.0 
EndSection 

Section "Screen" 
  Identifier "Default Screen" 
  Monitor "Configured Monitor" 
  Device "Configured Video Device" 
  DefaultDepth 24 
  SubSection "Display" 
  Depth 24 
  Modes "1024x768" "800x600" 
EndSubSection 

EndSection 

It works for an SP6000 which has the same card. (Found it here btw: [http://kimharding.net/dual_boot/](http://kimharding.net/dual_boot/))

---

