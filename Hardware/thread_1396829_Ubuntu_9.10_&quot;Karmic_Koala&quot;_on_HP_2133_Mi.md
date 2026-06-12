---
title: "Ubuntu 9.10 &quot;Karmic Koala&quot; on HP 2133 Mini netbook"
date: 2010-02-02
forum: Hardware
---

### Post by Igor Simic on 2010-02-02
Just installed Ubuntu 9.10 "Karmic Koala" on HP 2133 Mini netbook.
Resized existing win paritions with Acronis Partition Expert, to free some space for Ubuntu.
Installed with Grub dual boot without any problems.
All hardware - Ok.
Small problems were with video, some manual adjustments of XOrg and Gnome was neccessary.

There are some problems with samba... apparently it don't works with wireless connection, but I am not sure... need to play litlle bit.
Also, some strange behavior with suspend and hibernate, needs deeper investigation.
I'm running my corporate Lotus Notes 6.xx in Wine, with data on SD card... proud on this!

Ubuntu rulez!

---

### Post by Igor Simic on 2010-02-09
More experienced now:
  Sound does not work after suspend/hibernate.
  Alsa restart not solving problem. Sound card driver?

Video starts acting strange (Gnome desktop larger than screen) after installation of wireless card driver.
Fix: 
  line in /etc/X11/xorg.conf
  in section "Device" line Option "PanelSize" "1024x600"
  
WiFi and ethernet cards works perfectly, for Wifi used Broadcom STA wireless driver.
Bluetooth working.
Card reader working.
WebCam working.
:)

---

### Post by slipdipper on 2010-03-28
thanks for the update, any news on the external vga and fix for the sound? also are you using the via chrome9 drivers?

---

### Post by nvarras7 on 2010-04-10
10.04 beta2 fixed these issues for me.

---

