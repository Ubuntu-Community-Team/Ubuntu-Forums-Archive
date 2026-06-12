---
title: "Sound Issues on Eee PC 904HA with Intel HDA 82801G"
date: 2009-01-03
forum: Hardware
---

### Post by openn0de on 2009-01-03
Hello,

I am having a strange sound issue on Ubuntu 8.10 with my sound. The problem only exists when using headphones. The headphones get a large amount of loud static. I have an Eee PC 904HA with an 82801G Intel HDA sound interface. I am stumped with how to solve this problem. 

```
aplay -l
```
gives me this- **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and ```
lspci
```
gives this- 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

Thanks to the Ubuntu team for making Ubuntu so user friendly, my Install from a USB thumbdrive took about 10 minutes!

---

### Post by openn0de on 2009-01-03
Bump

---

### Post by openn0de on 2009-01-03
Bump... Can anyone help?

---

### Post by Sami_Sdata on 2009-01-03
Have you tried muting the various inputs while listening to the headphones?  I was getting a buzz on mine that ended up being from one of the inputs.  I think it was the front mic but not positive.  My problem was on a 900 so similar hardware at least.

---

### Post by openn0de on 2009-01-03
Thank you for the response, but this doesn't fix my issue. I am also not quite sure if I am using the right sound server, but I am muting the Mic Boost and capture channels on ALSA.

---

### Post by openn0de on 2009-01-04
Bump, Note: My Internal Microphone does work.

---

### Post by openn0de on 2009-01-04
Bump again. :(

---

### Post by Macchi on 2009-02-15
We have similar problems around here. I cannot get the sound to work perfectly on EEE PC 900 nor on the 701. The build in microphone does not work on Ubuntu despite several attempts to fix it. (The hardware is fine and works on Xandros). 

This is sad because skype is a very important communication solution for us at work and among family & friends.

---

### Post by openn0de on 2009-03-01
I would just like to put in that the issue exists not only in Ubuntu, but also in Fedora 10, and Sugar on a Stick. Static is only over headphone jack, all other sound components work.

---

### Post by openn0de on 2009-03-01
I am coming to a conclusion that this issue is just a badly shielded wire for the audio jack, and not a software issue. I will investigate further, thanks for all your help!

---

### Post by fuzecx on 2009-03-14
My sound works fine on my 904HA. Didn't have to install any drivers. No wireless though.

---

### Post by slimx3m on 2009-04-13
make sure that your wireless hardware is enable

---

