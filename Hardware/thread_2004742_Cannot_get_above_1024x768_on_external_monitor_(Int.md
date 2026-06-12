---
title: "Cannot get above 1024x768 on external monitor (Intel HD3000 Video)"
date: 2012-06-16
forum: Hardware
---

### Post by SybrJH on 2012-06-16
I have a Toshiba L755-S5110 notebook with Intel HD3000 video chipset hooked up to an Samsung 22" HDTV (via the VGA port) that I'm using as my main monitor. The problem is that I cannot seem to get a resolution higher than 1024x768. In Windows 7, I can get up to 1280x1024 fine. The TV is capable up to 1680x1050RB but I'd settle in getting 1280x1024 working. Running fresh install of Ubuntu 12.04 64-bit.  Any help would be gratefully appreciated.

---

### Post by Redblade20XX on 2012-06-16
How are you changing the settings?
Take a look into a program call: ARandR. It's in the software center.

-Red

---

### Post by SybrJH on 2012-06-17
Hmm. ARandR, only shows 1024x768 max resolution too as well as "Display" under system configuration. :( How can I tell which Xorg server is being used (ie, Intel, or Vesa)? I used to be able to tell via the xorg.conf file but I can't seem to locate it - not in /etc/X11. Any ideas?

---

### Post by jerrylamos on 2012-06-22
My TV monitor specs are 1366x768 ubuntu systems display says "unknown" and lists max 1024x768.  That's better than the netbook's 1024x600 but not as good as it could be.

Anyway to tell ubuntu what resolution to set?  Xrandr is no help, 1024x768 max, ARandR says it is a "screen layout editor" and crashed, apport in process: 

"Cannot connect to crash database, please check your Internet connection.

<urlopen error <urlopen error [Errno 8] _ssl.c:392: EOF occurred in violation of protocol>>"

This is wireless WPA running fine.

Any ideas?

Thanks, Jerry

---

### Post by SybrJH on 2012-06-25
Update: I get the full 1680x1050 as well as 1280x1024 and 1360x768 using a HDMI connection from the notebook to the HDTV rather than the RGB connection. This will work for now, but since the TV only has one HDMI input and that is being used by the cable set top box I've had to acquire a HDMI A/B switcher to toggle between the notebook and the set top. Not a desirable method but I guess it will have to do.

---

### Post by jerrylamos on 2012-06-25
Laborous solution:  No HDMI connector on my netbook.  So, 

xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1366x768_60.00
xrandr --output VGA1 --mode 1366x768_60.00

on every reboot or relogon.  I've put the commands into .xprofile but they are ignored.  So I use an exec with those commands.

I've put the monitor settings into /etc/X11/xorg.conf but they are ignored.

As far as I can tell, Quantal Quetzal never uses .xprofile or xorg.conf.

Laborious but usable.

Jerry

---

