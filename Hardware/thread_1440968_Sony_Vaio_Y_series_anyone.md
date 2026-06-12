---
title: "Sony Vaio Y series anyone?"
date: 2010-03-28
forum: Hardware
---

### Post by avilella on 2010-03-28
Anyone with a Sony Vaio Y series: VPCY11M1E/S, VPCY118GX/BI, VPCY115FX/BI, etc?

---

### Post by samjury on 2010-08-08
VPCY115FG Runs well.. Except no sound from speakers.

Sound card is;
Codec: Realtek ID 275
Codec: Intel G45 DEVCTG

Sound works through HDMI + 3.5mm but not through speakers.

---

### Post by samseh on 2010-09-11
see this thread to fix micrphone-- 

[http://code.google.com/p/vaio-f11-linux/issues/detail?id=2#c47](http://code.google.com/p/vaio-f11-linux/issues/detail?id=2#c47)

---

### Post by gotamangoflavouredrat on 2011-03-12
> **samjury said:**
> VPCY115FG Runs well.. Except no sound from speakers.

Sound card is;
Codec: Realtek ID 275
Codec: Intel G45 DEVCTG

Sound works through HDMI + 3.5mm but not through speakers.

On a VPCYB15AG , what worked out of the box

wifi, basic video, bluetooth
What works after two days of tinkering

Video , had to download the correct driver from amd.com and it works fine ( have not tried compiz, dont really need that )

Touch Pad - enable it by using instructions here [http://ubuntuforums.org/showpost.php?p=10123051&postcount=1](http://ubuntuforums.org/showpost.php?p=10123051&postcount=1)
Cannot scroll up using the touchpad, it just rapidly scrolls to the bottom of the page, tried updating the synaptics driver and installed gpointing-device-settings , no luck

AUDIO - Works weakly using headphones, the audio is ****  . Not a sound out of the speakers! tried everything ,  including this one [http://www.bytechip.com/2010/07/ubuntu-sony-vaio-audio/](http://www.bytechip.com/2010/07/ubuntu-sony-vaio-audio/)
no luck

does anyone have working sound out of the speakers on this vaio?



output of lspci
```
 00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
 
```

---

### Post by jandac2011 on 2011-03-22
After a week of searching, I do have good sound from the speakers. Use HDA-Analyzer, and set VREF in Node [0x19] PIN to either GRD or HIZ (both work). You can probably use hda-verb to set it during boot or logging in. This is for Sony Vaio VPC YB1S1E.

I still have no input from a microphone.

---

### Post by gotamangoflavouredrat on 2011-03-23
> **jandac2011 said:**
> After a week of searching, I do have good sound from the speakers. Use HDA-Analyzer, and set VREF in Node [0x19] PIN to either GRD or HIZ (both work). You can probably use hda-verb to set it during boot or logging in. This is for Sony Vaio VPC YB1S1E.

I still have no input from a microphone.

Any idea how to identify which PIN needs to be manipulated, when using HDA -Analyzer ? That would be helpful advice which will let others follow the path to your solution or at least test it

---

### Post by jandac2011 on 2011-03-23
> **gotamangoflavouredrat said:**
> Any idea how to identify which PIN needs to be manipulated, when using HDA -Analyzer ? That would be helpful advice which will let others follow the path to your solution or at least test it
An ideal would be to have a script that tests all possible values, e.g. using hda-verb. I found a solution asking dr. Google about similar problems in similar computers. The external microphone can be made to work by unmuting Val0 in Node[0x23] AUD_MIX in HDA-Analyzer, see [http://ubuntuforums.org/showthread.php?t=1712332]("http://ubuntuforums.org/showthread.php?t=1712332").

---

### Post by gotamangoflavouredrat on 2011-03-23
> **jandac2011 said:**
> After a week of searching, I do have good sound from the speakers. Use HDA-Analyzer, and set VREF in Node [0x19] PIN to either GRD or HIZ (both work). You can probably use hda-verb to set it during boot or logging in. This is for Sony Vaio VPC YB1S1E.

I still have no input from a microphone.

Got sound coming out of the speakers on a VPCYB15AG using the solution above, prior to that there was audio from the headphones only. The built in microphone works, but has a lot of static, you can barely make out what is being said ( almost like a bad shortwave radio station )

Tried to make this change permanent using 
hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22  from, [http://ubuntuforums.org/archive/index.php/t-1440444.html](http://ubuntuforums.org/archive/index.php/t-1440444.html)
The command does not work as I guess I should have tried it with su -c, cannot try it at the moment

---

### Post by jandac2011 on 2011-03-23
> **gotamangoflavouredrat said:**
> Got sound coming out of the speakers on a VPCYB15AG using the solution above, prior to that there was audio from the headphones only. The built in microphone works, but has a lot of static, you can barely make out what is being said ( almost like a bad shortwave radio station )

Tried to make this change permanent using 
hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22  from, [http://ubuntuforums.org/archive/index.php/t-1440444.html](http://ubuntuforums.org/archive/index.php/t-1440444.html)
The command does not work as I guess I should have tried it with su -c, cannot try it at the moment
I had similar experience with a noisy input from an **external** microphone, but the **internal** one does not work for me. Use the mixer, and decrease input volume and boost. As to hda-verb, it has to be run as root. It is a pity that HDA-Analyzer does not produce hda-verb commands with an additional button. hda-verb is quite cryptic, so guessing the exact names and values from the current diff output of HDA-Analyzer is at least difficult, and at the same time we need hda-verb to make the changes permanent until a new version of alsa comes with a model parameter for our audio card.

---

### Post by jandac2011 on 2011-03-24
> **gotamangoflavouredrat said:**
> Got sound coming out of the speakers on a VPCYB15AG using the solution above, prior to that there was audio from the headphones only. The built in microphone works, but has a lot of static, you can barely make out what is being said ( almost like a bad shortwave radio station )

Tried to make this change permanent using 
hda-verb /dev/snd/hwC0D0 0x19 SET_PIN_WIDGET_CONTROL 0x22  from, [http://ubuntuforums.org/archive/index.php/t-1440444.html](http://ubuntuforums.org/archive/index.php/t-1440444.html)
The command does not work as I guess I should have tried it with su -c, cannot try it at the moment
Your command using hda-verb does not work the way you meant.

---

