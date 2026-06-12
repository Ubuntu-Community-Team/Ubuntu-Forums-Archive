---
title: "Monitor Crashes with system shutdown"
date: 2018-10-30
forum: Hardware
---

### Post by ursaca on 2018-10-30
Hello,

Whenever I shutdown Ubuntu 18.4 LTS, my Monitor (ASUS 258Q) crashes to a blank Screen. I am not able to turn the Monitor off or change its input Source or access the Menue. 

My GPU is a RX580 TOP also from Asus. 

I am pretty sure the Problem ist Ubuntu related, because whenever I shutdown Windows at the same machine (different SSD) everything Works Fine. 

Thanks in advance!

Edit: Typo

---

### Post by vidtek on 2018-10-30
> **ursaca said:**
> Hello,

Whenever I shutdown Ubuntu 18.4 LTS, my Monitor (ASUS 258Q) crashes to a blank Screen. I am not able to turn the Monitor off or change its input Source or access the Menue. 

My GPU is a RX580 TOP also from Asus. 

I am pretty sure the Problem ist Ubuntu related, because whenever I shutdown Windows at the same machine (different SSD) everything Works Fine. 

Thanks in advance!

Edit: Typo

Ursaca-

Please state:
1) How is your computer connected to the monitor?  HDMI,Displayport,DVI,VGA????
There are signals sent to the monitor from both Displayport and HDMI, less so from a DVI connection, and none at all from a VGA connection with regard to energy-saving.
2) What flavour of Ubuntu-desktop?
3) Windows version which does not exhibit the same issue?

As a newbie-it would be very helpful for you to create a signature with your computer details and apply them to your posts-see mine below.

Thanks, Tony.

---

### Post by ursaca on 2018-10-30
Thanks for your answer! 

1) The Monitor is connected via DisplayPort 
2) I am using the default LXQt one. 
3) Windows 10 with most recent Update. 

Thanks for the tip! Will append my signature!

Since I can not change my Signature (10 Post Rule) here is my system!

Ryzen 2700x
Asus Crosshair Hero VII
16 GB DDR-4 3200 MHz G.Skill Trident Z
Asus Rog Strix RX580 Top Edition 
SSD 860 Evo 500 GB - Ubuntu 64 Bit 18.4 LTS default Flavor
SSD 970 Evo 250 GB - Windows 10

---

### Post by vidtek on 2018-10-30
OK, so what seems to be happening is windows is not sending a shutoff/sleep signal when it exits, but Ubuntu is.
You will need to go into your settings/configuration application for LX (I'm not familiar with this flavour) and check out the power, logon/logoff and display settings.
Start by putting them all on full power, no sleep or standby and then by a process of elimination see which setting is causing your problem.
As you are using Nvidia card, use the full power option on nvidia-settings too.  Then work backwards to see which works.

Tony.

---

### Post by ursaca on 2018-10-30
Thanks for your reply!

I Need to correct my Ubuntu Flavor! I am using Gnome Not LXQt! Sorry about that. My GPU is an AMD Card. 
Any additional Tips are very helpful!

Thanks in advance!

---

### Post by vidtek on 2018-10-30
> **ursaca said:**
> Thanks for your reply!

I Need to correct my Ubuntu Flavor! I am using Gnome Not LXQt! Sorry about that. My GPU is an AMD Card. 
Any additional Tips are very helpful!

Thanks in advance!

AMD has a similar application, go into it and adjust the power/fan/sleep/standby settings within it.  Gnome has a great interface for power settings and sleep/standby/logon (but nowhere near as good a KDE!  Plasma just rocks).

Tony.

---

