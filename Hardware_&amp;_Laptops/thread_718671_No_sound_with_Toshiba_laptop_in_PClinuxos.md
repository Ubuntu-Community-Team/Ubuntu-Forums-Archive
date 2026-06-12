---
title: "No sound with Toshiba laptop in PClinuxos"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by Istonian on 2008-03-08
I just installed PCLinuxOS after Ubuntu gave me no sound on my laptop. PCLinusOS is giving me the same problem. Here is my lspci.


Here is my lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by BobSongs on 2008-03-08
Love your Vista Lite quote.

Uhm, I assume you're aware these are the Ubuntu Forums, and not the PCLinuxOS forums, right? I'm not trying to be a jerk or unkind. It may just be an oversight. This happens when subscribed to several forums.

Have you tried [this spot]("http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26") first without success?

What PC type do you have? Laptop? Desktop? Model, etc?

---

### Post by LuisGMarine on 2008-03-08
Try this post, has helped me and all my friends running toshiba laptops.

[http://ubuntuforums.org/showthread.php?t=715301](http://ubuntuforums.org/showthread.php?t=715301)

---

### Post by gargy2002 on 2008-03-08
I have Toshiba A100-049 and everything works properly. I have even the same sound card like you and it works. On the cz forum one guy solved problem with a Toshiba laptop and sound card. There was probably problem with the restricted driver for wireless card(wifi turned off and sound works). Try to install the newest alsa driver(alsa-base, alsa-utils). 
I have also tried PCLOS(KDE) and I had the same problem with sound but the newest release with gnome works fine...

---

### Post by Istonian on 2008-03-08
> **BobSongs said:**
> Love your Vista Lite quote.

Uhm, I assume you're aware these are the Ubuntu Forums, and not the PCLinuxOS forums, right? I'm not trying to be a jerk or unkind. It may just be an oversight. This happens when subscribed to several forums.

Have you tried [this spot]("http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26") first without success?

What PC type do you have? Laptop? Desktop? Model, etc?

I know this is the ubuntu forums, but I posted the same thing in PCLinuxOS forums and noone could help me. I love this community.

---

### Post by Yellow Pasque on 2008-03-08
Have you tried configuring your alsa-base file like this thread suggests?:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

It also might help to upgrade to the latest ALSA. Here are some scripts to make that easy for you:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by Istonian on 2008-03-10
Alright, I am running Ubuntu on the lappy and still no sound. Any ideas? Tried previous ideas already.

---

### Post by Istonian on 2008-03-10
bump^

---

