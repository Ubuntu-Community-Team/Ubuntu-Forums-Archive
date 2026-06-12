---
title: "Trouble with HP ze2315us"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by davebgimp on 2005-09-28
I have recently purchased a HP Pavilion ze2315us laptop and supposedly successfully created a dual xp/ubuntu install. I first tried this with the Breezy preview, which after installing and successfully getting past the login splash-froze when showing the gnome loading screen and the welcoming sound justs skips over and over.
So, I removed that install and used the latest CD of Hoary. The install also completes, but half the time, when booting, it gets stuck  while setting itself up and won't progress until I hit the return button. If I do get to the login, once I sign in, it hangs at the splash, basically just like in the Breezy preview.
Can anyone help me with this or offer me any advice? I basically purchased this laptop to install Ubuntu on and I'm tempted to return it if it's not going to work out.
I'm very new to Linux, so I would really appreciate any assistance I could get. 
Here's my specs:
> AMD Mobile Sempron processor 3000+ with PowerNow! 1.80GHz
512MB DDR SDRAM (2 x 256MB) at 333MHz; maximum memory 1024MB DDR SDRAM (2 x 512MB)
ATI RADEON XPRESS 200M IGP with 128MB DDR (shared)
60GB 4200
DVD±RW and CD-RW combo drive with Double Layer support
15.0" XGA TFT Brightview (1024 x 768) display
54g Integrated 802.11b/g wireless LAN with 125HSM/SpeedBooster and BroadRange support
2 Universal Serial Bus (USB) 2.0
Integrated 10/100Base-T Ethernet LAN (RJ-45 connector), high speed 56K modem (RJ-11 connector)
Integrated Altec Lansing speakers
Thanks.

---

### Post by paragon-cs on 2005-10-10
I had the same problem.  I have a slightly newer hp but it did consistently hang after install.  The problem is that the ATI driver install sucks.  In order to get anything you need to edit the xorg.conf file and add the Option "NoAccel" to the Device section.  Mine looks like this now:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "NoAccel"

At least that will let you get into gnome.  It certainly isn't accelerated..in fact its pretty darn slow.  But it works.  I understand some people have gotten acceleration features to work...I have tried multiple times and haven't.

I have everything solved on this laptop except the acceleration issue and totem/xine/mplayer/whatever consistently crashing X on start-up.

Sucks.

And that is something that will cause me to switch if it can't be resolved.

I understand that this problem is quite "across the board".

Hope this helps.

Keith

---

### Post by putz3000 on 2005-10-11
I am glad i got to see this post.  I have been asking about info on the ze2117-us and have gotten no where.  I was getting ready to attempt an install but it is clear to me that hp and ubuntu are not a very good mix in regard to many models.  It is very frustrating.  It appears that the live cd has a problem with the ati chipset as well.  As much as I dont want to I may look at suse or just stick it out with xp until there is more success with ubuntu & HP.  I assume it is deffinantly an ATI issue and not a kernal issue?  Also, does anyone know if it is a debian issue or just an ubuntu issue?

-Rob

---

### Post by davebgimp on 2005-10-11
Well, it looks like I'm not alone. I gave up and returned the laptop. I figured if no one was going to help, I'd rather not be stuck with a piece of junk running XP. Oh well. I guess when picking a new one, I'll go with the pre-tested models out there.

---

