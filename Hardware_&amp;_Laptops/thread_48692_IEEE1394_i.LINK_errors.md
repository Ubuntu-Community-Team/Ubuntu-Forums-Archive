---
title: "IEEE1394 i.LINK errors"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by JonasR on 2005-07-13
Please bear with me for I am a newby...

I recently installed Ubuntu and noticed everything works fantasticaly except my firewire CD writer. So I started searching for solutions. To date I did not find any. I did find the ominous warning that i.LINK from Sony is NOT supported (on [http://www.linux1394.org)](http://www.linux1394.org)). Since I have a Sony Vaio (PCF F807K if that means anything to anyone) this worried me. However, it went on to say:

> Please note as well that not all Sony VAIO systems use the proprietary chip. Some contain the CXD3222, which is reported to be OHCI compliant.

I went to my Device Manager and found a "CXD3222 i.LINK controller". To me this implies that my controller is OHCI complient, and therefore should work with the 2.6.10-5-386 kernel as comes with Hoary 5.04.
So I did some experimenting. When I hotplug-in the firewire drive, at the end of dmesg it says:

> ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node resumed: ID:BUS[0-01:1023]  GUID[0001db0250000bb8]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
scsi4 : SCSI emulation for IEEE-1394 SBP-2 Devices

After about twenty seconds dmesg also reports:

> ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
sbp2: probe of 0001db0250000bb8-1 failed with error -16

This happens both with and without a CD in the drive.
When I unplug the drive, dmesg says:

> ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0001db0250000bb8]

I don't know what else to do or to mention here, except that the cd writer in question is a Freecom classic series CD-RW.

Any help will be most appreciated!

---

### Post by scoon on 2005-07-14
Hey there, 

Good luck w/ that one.  linux1394 is pretty accurate.  So you may not beable to get it to work.  

regards, 

scoon

---

### Post by JonasR on 2005-07-14
Thanks Scoon,

if linux1394 is indeed accurate, this rather means that it *should* work, since my i.LINK contains the CXD3222 chip, which should be OHCI compliant. linux1394 states:
> The supported chipsets are ... and OHCI compliant chips  
I also recall using my CD RW drive successfully some time ago on Red Hat with kernel 2.4.x, so I'm guessing the problem is elsewhere.
Any help, anyone?

---

### Post by scoon on 2005-07-14
Hey there, 

Have you gone over the trouble shooting steps that they suggest.  It could just be that ubuntu does NOT load all of the necessary modules.  You can check that with lsmod.

regards, 

scoon

---

### Post by JonasR on 2005-07-17
lsmod says these are loaded:

Module                  Size  Used by
ohci1394               31876  0 
sbp2                   22408  0 
scsi_mod              119936  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2

so I seem to be missing libraw1394. As I said at the beginning I'm a newby - I have no idea whatsoever how to get libraw1394 going, nor whether it is necessary or related to this problem. Nor does linux1394.org give directions on how to actually do stuff (at least none that I understand).
I do know that [this google search](http://www.google.nl/search?q=1394+%22+failed+with+error+-16%22)  gives me the answer that I'm not the only one running into this error with ieee1394. However, no answers that I can find in that direction either. 
[The third hit](http://lists.debian.org/debian-kernel/2005/04/msg00556.html) suggests that this problem originates in kernel 2.6.10. 
I'm stuck on what to do next...

---

### Post by scoon on 2005-07-17
Hey there, 

Try modprobe -v raw1394.  the linux 1394 site does say to try that. 

regards, 

scoon

---

### Post by JonasR on 2005-07-24
Sorry I didn't get a chance to try until tonight, here's what I can tell:

modprobe -v lib1394 gives the following message:
> insmod /lib/modules/2.6.10-5-386/kernel/drivers/ieee1394/raw1394.ko

lsmod now reports:
> raw1394                28652  0

dmesg says:
> ieee1394: raw1394: /dev/raw1394 device initialized

Earlier in dmesg it reported (I guess during boot-up):
> ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:00:08.0 (0000 -> 0002)
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 9 (level, low) -> IRQ 9
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[fedff000-fedff7ff]  Max Packet=[2048]
ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001db0250000bb8]
ieee1394: Host added: ID:BUS[0-01:1023]  GUID[08004603005471c1]
scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices


Unplugging the CD-RW generates the following dmesg lines:
> ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0001db0250000bb8]


Plugging it back in gives the usual string in dmesg:
> ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0001db0250000bb8]
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
scsi1 : SCSI emulation for IEEE-1394 SBP-2 Devices


And about 20 seconds later:
> ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
sbp2: probe of 0001db0250000bb8-1 failed with error -16

 ](*,)

---

### Post by JonasR on 2005-08-09
Has anyone got any more ideas/tips what to do about this problem? I am very happy with Ubuntu but if it cannot work with my CD writer I'll be forced to try out other distro's, which would really disappoint me!
Any help please? If more info is needed, please tell me what.

---

### Post by petr on 2005-09-21
[QUOTE=JonasR]Has anyone got any more ideas/tips what to do about this problem? I am very happy with Ubuntu but if it cannot work with my CD writer I'll be forced to try out other distro's, which would really disappoint me!
Any help please? If more info is needed, please tell me what.[/QUOTE]
 peripheral evidence of a problem with ubuntu,  I used to use Debian and didn't have a problem with the i.link port on a vaio PCG 505 FA. (5 years old)  I have never got the memory stick port to work, which apparently plugs into the PCI bus.

petr

---

### Post by JonasR on 2005-10-03
Upgrading to the Breezy Badger preview has sorted this problem for once and for all. I am now happily burning CD's again.
Also: Breezy Badger rules! :D

---

### Post by petr on 2005-10-03
Glad you got it fixed.  I will look at Breezy Badger...
Otherwise I am going to have to join the hackers working on Puppy.

Petr

[QUOTE=JonasR]Upgrading to the Breezy Badger preview has sorted this problem for once and for all. I am now happily burning CD's again.
Also: Breezy Badger rules! :D[/QUOTE]

---

