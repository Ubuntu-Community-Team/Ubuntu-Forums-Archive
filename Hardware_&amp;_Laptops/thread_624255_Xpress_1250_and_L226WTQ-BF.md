---
title: "Xpress 1250 and L226WTQ-BF"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by dsundquist03 on 2007-11-26
Dear Community,

I was looking for some help... I just bought a LG L226WTQ-BF monitor and am having some issues getting it to display at 1680 x 1050.  For video i have an on-board 690g / Xpress 1250.  Ubuntu uses a plug and play driver for the monitor and when i goto select 1680 x 1050 the screen is gray and black (speckled) and displays a window in the upper left for me to keep the configuration or cancel with a x as the cursor.  The screen is much like that when X Server is loading on other versions of linux.  I have been using the ATI restricted drivers and have also tried not using them.  When i disable the restricted drivers i do not even have an option to select 1680 x 1050, only upto 1280 x 1024.  Any ideas?

Dean

---

### Post by kishoreg1980 on 2007-11-27
Hi,

I also bought this monitor recently and had trouble setting the resolution. I tried lot of things to fix this problem but dint find any place which solved this problem. I have nvidia geforce 6150. There are few things i did

First install driver for your video card. There are lot of ways you can do this. I did this System-> administration->Restricted Driver Manager
This will install the driver. 

sudo dpkg-reconfigure -phigh xserver-org
While choosing the resolution select 1680x1050 you can chose additional resolution but nothing more than 1680x1050

sudo vim /etc/X11/xorg.conf  
please back up your xorg.conf before editing it.

Under  "Device" section edit the driver value to reflect your video card. I changed mine to nvidia

Change Monitor section as below

Section  "Monitor"
    Identifier "LG L226WTQ"
   Option      "DPMS"
  HorizSync  80-93
  VertRefresh  60-75
EndSection

Hope this helps.
Enjoy your new monitor

---

### Post by dsundquist03 on 2007-11-27
Hrm..

Thats not exactly what im looking for.  I have my video card already installed.  And if i try to run the command i get:

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed


Any ideas? 

Dean

ps. I have an onboard ATI graphics card... and your running nvidia

---

### Post by dsundquist03 on 2007-11-27
I found out why that command isnt running... When i run xserver-xorg at the end it works.  However, i only have an option to select a driver.. and it is set at vesa...  and when i hit enter it exits out and doesn't goto a screen to allow me to change the resolution.

---

