---
title: "No DVD-ROM..."
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by samunai on 2008-03-12
Hello,

I can't accsses my DVD-ROM

I allways get the error message: "mount: special device /dev/cdrom does not exist"

here some informations about my configs and system:

DVD-ROM is connected via IDE on Master1
I dont have any other DVD drives
I can see DVD drive in BIOS

**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd06be83-4b2e-4768-8a51-729fb432fa54 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=36e52f19-ca65-4aa4-aca0-fae507b42f45 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

**dmesg | grep cd**
```
[    0.000000] Kernel command line: root=UUID=cd06be83-4b2e-4768-8a51-729fb432fa54 ro quiet splash
[   24.674500] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   24.674596] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   24.674621] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[   24.775961] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   24.775984] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   24.776010] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e000
[   24.879974] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   24.880000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   24.880036] ehci_hcd 0000:00:1a.7: debug port 1
[   24.880049] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xffaffc00
[   24.883919] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.987881] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.987906] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   24.987933] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000d480
[   25.091838] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.091860] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   25.091885] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d800
[   25.195764] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.195784] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   25.195805] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000d880
[   25.331652] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   25.747532] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   26.167404] usb 5-2: new full speed USB device using uhci_hcd and address 3
[   26.715571] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   26.715591] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   26.715615] ehci_hcd 0000:00:1d.7: debug port 1
[   26.715625] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffaff800
[   26.719507] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.063141] usb 7-1: new high speed USB device using ehci_hcd and address 2
[   27.994870] usb 5-1: new low speed USB device using uhci_hcd and address 4
[   28.414741] usb 5-2: new full speed USB device using uhci_hcd and address 5

```


In other board I've got the answer the line

**/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0**

in /etc/fstab is wrong and i have to replace it with **/dev/scd0** or similiar.

It didn't help. I tried also several others (scd1, sdb, ...). Didn't help.

In Hardinfo i don't see the device also.
[http://img152.imageshack.us/img152/4448/94666186pk3.png](http://img152.imageshack.us/img152/4448/94666186pk3.png)


Please help. Where can i lookup how is name of my device?
I can't understand why so simple things like DVD drive doesn't work out of the box...

P.S.: sorry for my bad english

---

### Post by NorthernLights on 2008-03-12
> Where can i lookup how is name of my device?

I use :

```
cdrecord --devices
```

[IMG]http://www.e-facile.fr/images/articles/cdrbq/07.png[/IMG]

---

### Post by samunai on 2008-03-12
> **NorthernLights said:**
> I use :

```
cdrecord --devices
```

[IMG]http://www.e-facile.fr/images/articles/cdrbq/07.png[/IMG]

thank, but as i understood it shows only record devices. My DVD drive cant record CDs or DVDs. It is read-only drive.

Anyway, i tried this command and got

```
cdrecord: No tracks specified. Need at least one.
Usage: cdrecord [options] track1...trackn

Use     cdrecord -help
to get a list of valid options.

Use     cdrecord blank=help
to get a list of valid blanking options.

Use     cdrecord dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use     cdrecord dev=help
to get a list of possible SCSI transport specifiers.
```

---

### Post by Dive4Life on 2008-04-16
I have been doing research on this very same problem.  Mine started occuring after a motherboard replacement.  BIOS detects both drives without a problem but UBUNTU can't seem to find them.  I was reading on other posts where some have managed to fix this through changing settings in BIOS.  I went through my BIOS and literally tried the hit or miss method to no avail.  Nothing from any of the previous posts other than this worked.  Hopefully one of us can figure this out.

---

### Post by samunai on 2008-04-16
I've solved the prob: bought a new SATA DVD-RW Drive :) 

I deleted the Ubuntu (not cuz of this prob) and installed windows xp again. Now, the old drive wont be detected by windows too.

greetz,
samunai

---

