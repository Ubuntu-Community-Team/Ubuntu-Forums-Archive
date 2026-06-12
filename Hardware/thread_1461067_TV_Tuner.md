---
title: "TV Tuner"
date: 2010-04-23
forum: Hardware
---

### Post by Millamber on 2010-04-23
I am a Windows System Administrator with a background in training. I am a recent convert to Linux. I have built a Ubuntu system for use as a media centre. I recently bought a TV card and I am having trouble understanding how to get it working.
 
I am looking for someone to help that doesn't mind starting with the basics and answering what might be seemingly stupid questions.
 
The Card: DNTV Dual Hybrid (7164) PCIe 
([http://www.digitalnow.com.au/dvbtcards.html](http://www.digitalnow.com.au/dvbtcards.html))
 
This card uses the same chipset as the Hauppauge HVR-2200 which apparently is supported but not out of the box.
([http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200))
 
I have tried the instructions in these posts to no avail.
([http://ubuntuforums.org/showthread.php?t=1167640](http://ubuntuforums.org/showthread.php?t=1167640))
([http://ubuntuforums.org/showthread.php?t=1167640](http://ubuntuforums.org/showthread.php?t=1167640))
 
From what I can work out the driver "was merged with the repository"?
([http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17))
 
If anyone is willing to help or provide some pointers it would be much appreciated.
 
Millamber

---

### Post by Directive 4 on 2010-04-23
hi, mines a Hauppauge.

just download tvtime from the software centre or such (me tv should work to)  i remember, kaffeine is the program you want

and scan for channels, should be plug and play, that threads a bit old. 


it helps a LOT if you plug it into your house aerial for the scan for channels part,


my advice,

stay away from myth tv,

unless you got a weekend to spare and don't want to watch any tv:lolflag:

---

### Post by Zyphrexi on 2010-04-23
if the driver was merged with the repository, you could try modprobe or insmod.

EDIT: err I was thinking kernel. disregard that

---

### Post by coffeecat on 2010-04-23
> **Millamber said:**
> This card uses the same chipset as the Hauppauge HVR-2200 which apparently is supported but not out of the box.
([http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200))
 

I have a Hauppage DVB-T card with a Phillips chipset. The output of lspci gives me:

> 01:06.0 Multimedia controller: Philips Semiconductors  SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)Which is not the same as yours but, yours being a Philips, you may be lucky with the same fix I discovered. With Karmic, it's not the driver that's the problem - it's the firmware which is non-free and can't be included in a default install. If you're running Karmic (or Lucid), install the package linux-firmware-nonfree to get the firmware and then, hopefully, you'll be good to go.

If you're running Jaunty though, this won't help because in Jaunty both the free and nonfree firmware came in the box.

Note - I see that in that above link there were instructions on how to install the firmware from steventoth.net. Did you try that? If not, it's probably easier installing the Ubuntu package.

---

