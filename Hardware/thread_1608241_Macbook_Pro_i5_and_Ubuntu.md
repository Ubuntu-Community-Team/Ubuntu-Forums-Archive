---
title: "Macbook Pro i5 and Ubuntu"
date: 2010-10-28
forum: Hardware
---

### Post by vsh3r on 2010-10-28
Hi,

I recently installed Ubuntu 10.10 on my Macbook Pro 6,2 i5 (quad core) laptop.

WHAT WORKS:
+64 bit Ubuntu
+webcam (skype)
+microphone (edit /etc/modprobe.d/alsa-base.conf to include "options snd-hda-intel model=mbp55")
+wireless (some connection issues)
+cdrom burning
+printers (network/usb tested)
+display (NVIDIA)
+AWN (difficult to add icons)

WHAT DOESN'T WORK:
+function keys (pommed)
+startup screen (i915 error)
+bluetooth 
+external display (haven't tested)

(INSTALL:[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick))
(EFI UPDATE: [http://support.apple.com/kb/DL1098](http://support.apple.com/kb/DL1098))

QUESTIONS:
1. How do I get POMMED working so I can use my function keys?
2. Is there anyway to easily get BLUETOOTH working using the synaptic package manager?  Has anyone else tested bluetooth on the i5 Macbook Pro's?
2. SOMETIMES The computer doesn't seem to recover from SLEEP MODE?  I believe this is a bug on OSX as well.  Apple recommends I do an EFI update ... however, is there a way to install the EFI update without installing OSX?  

Does anyone else have any suggestions for Macbook Pro i5's?  All 4 of the CPU's seems to be running at around 10% to 20% when idle?  Does this seem normal to people for a quad core?

Thanks!
V$h3r

---

### Post by vsh3r on 2010-10-28
[IMG]http://asherm.com/blog/wp-content/uploads/2010/10/Screenshot-System-Monitor.png[/IMG]

This shows the task manager while my system is idle... however, all 4 CPU's seem to fluctuate between 10% and 20% use.  I would be interested to see an OSX view or perhaps a non-macbook pro i5 system or AMD Quad Core.  I have maybe 5 programs open but they are really all idle and not doing anything.

If anyone figures out POMMED on the Macbook Pro 6,2 let me know.

V$H3r

---

### Post by vsh3r on 2010-10-30
Hi,

I've done a system wide update using MAC OSX and after doing this the LED display brightness function keys work without the MAC OSX update 10.6.4 the keys didn't work in Ubuntu 10.10.  This must be an Apple bug.

Here is a listing of what HardInfo says about the system:

Computer Processor4x Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz Memory3915MB (880MB used) Operating SystemUbuntu 10.10  
DMI BIOS Date07/26/10 VendorApple Inc. ([www.apple.com](www.apple.com)) VersionMBP61.88Z.0057.B0C.1007261552
My network connection still seems a LOT SLOWER on UBUNTU then OSX when I first start OSX.  OSX seems to connect very quickly as soon as it boots up while Ubuntu 10.10 has some hesitation.

The Firmware Version for my wireless card is: Broadcom BCM43xx 1.0 (5.10.131.16.1)


Thanks!
Vsh

---

### Post by vsh3r on 2010-10-30
HardInfo says that my wireless card is:
Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)

Is this the same as the one that OSX thinks it is?

Thanks,
Vsh

---

