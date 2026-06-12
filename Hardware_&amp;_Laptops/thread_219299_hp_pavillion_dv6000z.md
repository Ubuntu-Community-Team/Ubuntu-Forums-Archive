---
title: "hp pavillion dv6000z"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by markybob on 2006-07-19
anyone know if the new hp pavillion dv6000z work well with linux?  i havent been able to find any information at all by using google and i'd like to buy this laptop if it works.  thanks!

---

### Post by reacocard on 2006-07-19
i have a dv4000 and it works perfectly with ubuntu.

---

### Post by markybob on 2006-07-19
thanks, but they dont make the dv4000 anymore, so in my eyes its likely that the 6000 has a different motherboard/chipset, etc.

---

### Post by reacocard on 2006-07-19
yes, but they are similar. a quick search in the wiki turns up serveral other hp pavilion laptops which all seem to work fairly well. be sure to get the intel wireless, since it works automatically, while the broadcom wireless requires ndsiwrapper.

---

### Post by a-nubi-s on 2006-07-20
I want to ask the same thing, but for the [dv8000z]("http://www.notebookreview.com/default.asp?newsID=2681").

---

### Post by reacocard on 2006-07-20
see what i said above. hp pavilion laptops seem to work well, if you get the intel wireless.

---

### Post by wumarkus on 2006-08-27
I'm trying to keep-up with a wiki page I have on the dv6000z:

[http://wiki.wumarkus.com/index.php?title=HP_Pavilion_dv6000z_Laptop_Stuff](http://wiki.wumarkus.com/index.php?title=HP_Pavilion_dv6000z_Laptop_Stuff)

It does not work particularly well with Linux so far. There is a constant BIOS BUG error and constant lockups unless you use acpi=off in your grub config when booting the kernel. The bcm43xx driver isn't working at all. I'm looking at trying the new bcm43xx branch with the latest test kernel to see if we can get a working native driver, since I wasn't even able to get ndiswrapper to work.

---

### Post by |)arkFire on 2006-09-01
I recently did a clean install from the dapper 64 Alternative cd (due to consistant lock ups during install from the gui cd).  Smooth installation, some boot problems with grub (must have pci=noacpi), and the interface is functional. There is a bit of work getting the inital network set up and yes, b/c of broadcom, the wireless is still in need of configuration (any help would be great). But needless to say thanks to ubuntu very little has to be manuely configured for the dv6000z to be operational.


edit: I just realized that the sound is not working either. So the install is not 100% successfull but hey, it's better than nothing, happy configuring.

---

### Post by martinrandau on 2006-09-01
I think that the acpi=off is what disables both the wlan device and the sound, sadly enough. I abandoned ubuntu and tried with suse for that same computer and got it everything working by passing noapic to the kernel. You might wanna try this. I didn't try it on ubuntu, but had it worked I'd stuck with it of course! :D

---

### Post by Lanfeust on 2006-09-10
Indeed the noapic option worked for me.  Got the sound card working, but only with the laptop speakers.  The headphone jacks seem to be disabled or not actived as well the line-in jack.  

I have been unable to make the wireless card working, neither with ndiswrapper or with the bcm43xx module.  Moreover, bcm43-fwcutter doesn't recognize the bcmwl5.sys file (from the C:\SWSetup\WLAN directory) as its version is too high.

---

### Post by |)arkFire on 2006-09-12
Lanfeust, what did you end up doing in order to get the sound to work?

---

### Post by Lanfeust on 2006-09-21
Nothing, really.  In fact, the sound worked directly with that noapic keyword (so no acpi=off option at the boot), even the special keys (mute, vol down and up) and the IR remote control.  The snd_hda_intel driver is loaded automatically.

---

### Post by haxx on 2006-09-21
a little trick but if your willing i got ya set

---

### Post by |)arkFire on 2006-09-24
" The snd_hda_**intel** driver is loaded automatically."

oh, i take it you have the dv6000 not the dv6000z, oh well

---

### Post by Lanfeust on 2006-09-26
I have the dv6000**z** (with AMD Turion(tm) 64 X2 Mobile Technology TL-52).  by the way, but there's none dv6000, it's either dv6000z (AMD) or dv6000t (Intel).

The sound card is a conexant (id 14f1:5045), based on the High Definition Audio (HDA) ship from intel and the driver that is recognized is the snd_hda_intel.  However, this driver (even in version v1.0.12rc2, latest stable alsa version, with the kernel 2.6.15-27) cannot handle all the features of the card.

By the way, now I'm running KUbuntu (not the 64 bits version).  Sound still working, but the special keys for the sound and the remote control are not working anymore.

---

### Post by ZERO_SHIFT on 2006-09-26
I need some advice as whether or not hp dv8000t would work properly with linux:
wireless
Bluetooth
nVidia Graphic card
...etc

please advice whether its ok or no.

Thanks In Advance.(TIA)

---

### Post by Lanfeust on 2006-09-27
This link [http://cepes.org.pe/jaime/dv8000t.html](http://cepes.org.pe/jaime/dv8000t.html) could help you.

---

### Post by stebnera on 2006-10-08
I too am a dv6000z owner. I have the wireless working great in Ubuntu by using ndiswrapper and the drivers for the wireless chipset that are packaged by Dell. The drivers HP packages will not work. You can get the drivers from the link at the ndiswrapper website or directly from Dell's website. The chipset is BCM4310 UART (rev01). Once I had these drivers, I followed the howto here: [http://www.seungpyo.com/stacksandpiles/2006/07/02/](http://www.seungpyo.com/stacksandpiles/2006/07/02/)

I too am having sound card issues though. The soundcard works with M-Player, but as someone else noted my headphone jack won't work at all, nor will the headphone jack on my docking station, which is pretty annoying since I do a lot of musical editing (laptop speakers don't really cut it). Also, I can't get audacity to pick up my soundcard at all. If anyone finds a solution to get the soundcard to really function as designed I'd love to hear it. Thanks.

---

### Post by markybob on 2006-11-16
The headphone problem is a known bug in alsa 1.0.12rc1 (cat /proc/asound/version)...it'll be fixed when you install a kernel that has an updated alsa.

---

### Post by nbayiha on 2006-11-27
i have a hp dv6000 and i still didn't manage to make my wireless card work so if someone know a way to make it work...... don't be shy

---

### Post by muximus on 2006-11-27
have a hp pavilion myself.. everything works except for the on board speakers.. if u attach any speakers then they work no problem. maybe there is a solution somewhere which i am yet to see

---

### Post by teaker1s on 2006-11-28
after reading a lot of dis-jointed and mis-guided FUD about various HP DV6000 series laptops I have started a wilki page listing things I've found specifically the DV6116EU AND **YES BROADCOM 4311 REV 01 DOES WORK AT 54MB/S** perfectly
[HERE]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by emperon on 2006-12-13
No, it does not run perfectly. I have checked out your wiki. Unfortunately  (may be for most of them)  dv6000 series you cannot make nvidia drivers working together with ndiswrapper (for 32bit). If you do, you will get a conflict and you lose both network and X. The solution for this to use nosmp option which dramatically reduces the performance. So although it works, ndiswrapper is only a workaround and IS NOT the preferred method. I would have been delighted if native drivers  worked fine rather than messing with ndsiwrapper

UPDATE: This issue seems to be fixed with 2.6.19.1 kernel

---

### Post by x64Jimbo on 2006-12-16
Can anyone tell me if the bluetooth that comes built in is packaged in the Mini-PCI card that contains the wifi device, or if it is somewhere else? I want to put my a/b/g Atheros card into my system when I get it, but if the bluetooth is built into the broadcom card, I'll be SOL.

---

### Post by MethodMachine on 2007-01-07
> **emperon said:**
> No, it does not run perfectly. I have checked out your wiki. Unfortunately  (may be for most of them)  dv6000 series you cannot make nvidia drivers working together with ndiswrapper (for 32bit). If you do, you will get a conflict and you lose both network and X. The solution for this to use nosmp option which dramatically reduces the performance. So although it works, ndiswrapper is only a workaround and IS NOT the preferred method. I would have been delighted if native drivers  worked fine rather than messing with ndsiwrapper

UPDATE: This issue seems to be fixed with 2.6.19.1 kernel

This is exactly the situation I am facing at the moment (on a dv6113us with AMD Turion64X2, nVidia GeForce Go 6150, and BCM4311 wireless).

Kernel:

2.6.17-10-generic

Wireless:

Broadcom 4311--I was able to get the wireless working by compiling the latest version of ndiswrapper (v1.33) from source and using the windows drivers that came with the laptop.  Additionally, I installed network-manager and knetworkmanager (I use Kubuntu) and am able to reliably connect/reconnect to the various WAPs in my home with no problem.

nVidia Drivers:

I used nVidia's script to compile and install the drivers from the nVidia ftp site using instructions provided [here]("http://ubuntuforums.org/showthread.php?t=263851") using the instructions under Step 2, Option 2 (Option 1 resulted in really sluggish performance).

Unfortunately, actually using the nVidia drivers (which make the display look beautiful, by the way), makes the wireless basically unusable.  To use wireless, I have to revert back to xorg.conf.backup.


Moving forward:

I have been trying to compile and use kernel 2.6.19.1 since there are reports that may fix some of the problems.  Unfortunately, after two attempts I can't get a kernel that will actually boot.  Does anyone have any kernel configuration tips?

***UPDATE:***

After several attempts at getting a working kernel, it seems that enabling the **NVIDIA SATA support** module did the trick.  With kernel version 2.6.19.1 compiled and working, I then recompiled ndiswrapper from source (v1.33), removed the old reference to the wireless card drive (ndiswrapper -r bcmwl5), reinserted the driver (ndiswrapper -i bcmwl5.inf) and wireless is working fine.

nVidia drivers also work following the methods outlined in the link mentioned above.

---

### Post by tonyldo on 2007-04-17
Hello,
I saw the problems with this notebook on ubuntu  :-(  and i decide wait for the new version (Feisty) and then do my first ubuntu install o my hp dv6000z. 
Do u think that problems will disaper with this new version of ubuntu? There is another distro that work out of the box on this notebook?

I would like change my windows vista home basic by a linux SO but i dont have experience to do all necessary configuration. :confused:

---

