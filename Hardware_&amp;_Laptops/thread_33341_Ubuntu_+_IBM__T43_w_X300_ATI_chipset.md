---
title: "Ubuntu + IBM  T43 w/ X300 ATI chipset"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by vannguyen0 on 2005-05-10
Has anyone gotten 3D acceleration to work on Ubuntu w/ ATI's X300 chipset on an IBM ThinkPad.  I've search all over and found many forum postings that tells you how to do it with using fglrx... tried it all... but still only get the [www.mesa3d.org](www.mesa3d.org) as my video card when I do fglrxinfo.  I changed the setting in my /etc/X11/xorg.conf to reflect the fglrx.... 

I found one for the Dell, tried that and still no go.... =\

Very frustrated....

---

### Post by casoe on 2005-05-11
I have also big problems with a T43 and X300. I am able to start the XServer without problems or errors in /var/log/Xorg.0.log, but this leads me to a black und blank screen. I tried to switch 

Option          "MonitorLayout" "LVDS,NONE"

with the possible values, but nothings makes kdm say hello. So I am dealing with the ati driver from xorg at the moment, which brings big power consumption and poor 3d performance.

Frustrated,too.

---

### Post by Martey on 2005-05-23
If you look at your Xorg logfile, you will see that the blank screen when X is run with the fglrx drivers seems to be because the driver cannot find any monitors. Unfortunately, I do not know how to fix this.

---

### Post by casoe on 2005-05-25
I don't think that this is the problem. My Xorg.0.log ist rather clean. I just tried different configurations with internal and external AGP, different monitorlayouts and DDC enabled or disabled. I compiled a new kernel in different versions 2.6.11 clean, 2.6.11 with patches and the brand new 2.6.12.rc4, who brought compiling errors with fglrx. Nothings helps.

I hope this is only a general driver problem because the T43 is very new. Perhaps the next generation driver brings fixes for this problem.

I'm using die ubuntu hory kernel and the ati driver from Xorg 6.8.2 again.

Still very frustrated.

---

### Post by casoe on 2005-06-09
I'm looking for Options to tell X, which screen is first and which second. With fglrx it is allways the problem, that it detects secondary as primary dac.

---

### Post by shizow on 2005-07-20
[QUOTE=casoe]I have also big problems with a T43 and X300. I am able to start the XServer without problems or errors in /var/log/Xorg.0.log, but this leads me to a black und blank screen. I tried to switch 

Option          "MonitorLayout" "LVDS,NONE"

with the possible values, but nothings makes kdm say hello. So I am dealing with the ati driver from xorg at the moment, which brings big power consumption and poor 3d performance.

Frustrated,too.[/QUOTE]

did you try
Option "MonitorLayout" "LVDS,STV"

that worked with my t43

---

### Post by lynng on 2005-07-26
[QUOTE=shizow]did you try
Option "MonitorLayout" "LVDS,STV"

that worked with my t43[/QUOTE]

I did try this option with my t43, but the only difference was that the monitor comes on but stays blank.  Without that option the monitor doesn't appear to come on at all.

---

### Post by sml on 2005-08-30
Have you made any good progress with the T43 and X300.

My T43 is arriving tomorrow so any help would be appreciated.

---

