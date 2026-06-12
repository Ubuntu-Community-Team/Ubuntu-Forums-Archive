---
title: "ati 4250 driver choice? running unity.kde on a laptop!"
date: 2011-11-12
forum: Hardware
---

### Post by chaosengine on 2011-11-12
hi ubuntu forums,

I have just come back to ubuntu after my windows 7 system broke down on me. Won't be going back there in a hurry! 
So now i've installed ubuntu 11.10 and kde-standard. I dual boot with xp. So impressive, everything worked out of the box..sound, wifi the lot. I have an Acer Aspire 5552, 4gb ram, AMD x3 processor.

My** Q is, Can you guys explain which ATI driver I should be installing here? **The propitiatory ones in Jockey, or the catalyst's from ATI's website? or keep the default, open source drivers? I've had a search on the forum and found a right mix of advice!



I've heard a lot of problems with Gnome 3 and drivers, does this effect Unity and KDE 4.7.x and ATI gfx cards?
Also, something about the FAN's not being controlled properly on the gfx card in one of the drivers?

Hope u guys can clear this up for me. :KS

Kind regards,

---

### Post by chaosengine on 2011-11-12
mm I just saw on another forum that the open source drivers are not supporting support dynamic power management?

I just want to make the most of my hardware, shall I just plump for the drivers found in the additional hardware drivers (jocky)?

---

### Post by MoreOrLess on 2011-11-12
You should use whatever works best for you..

---

### Post by chaosengine on 2011-11-12
> **MoreOrLess said:**
> You should use whatever works best for you..
i agree, im just a little confused with options available! to continue with the open source drivers, which are working but without hdmi sound out, install the fglrx from addition hardware, or download the drivers and manually install the latest ones from ati.com?

I kinda wanted to hear what other people have done with ATI and ubuntu so I don't have to install one and have to mess about installing (again!)

---

### Post by Jefry on 2011-11-12
My Ideapad z565 notebook seems to have the same (or very close) graphics chipset. So far, the proprietary driver under Ubuntu 11.10 seems to be running stable. Using the VGA out instead of the HDMI out to 22" Samsung HDTV on the desktop (HDMI port is taken up by cable box). Gnome 3 is installed but the fonts on the title bar seems to be messed up when running default desktop. This happens with both the open source and proprietary graphics drivers =(. Switching to Gnome Classic Menus at the login screen works however I am not sure if that is running Gnome 3 in a backwards compatibility or an older version of Gnome? 

I hope that Ubuntu 11.10 works well. I too am trying to switch from Windows 7. 

-Jeff

---

### Post by MoreOrLess on 2011-11-12
To get HDMI audio working with open-source radeon, create a file /etc/modprobe.d/radeon.conf
Put this line in it, save, and quit your text editor.
```
options radeon audio=1
```
Then:
```
sudo depmod -a
sudo update-initramfs -u -k all
```
Cross your fingers and restart.

---

