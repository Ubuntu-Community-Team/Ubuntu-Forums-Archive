---
title: "Edgy mounts USB 2 devices as USB1"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by Usul_ on 2007-01-16
Hi everybody!
I have a  brand new Fujitsu Lifebook S2110 with Ubuntu 6.10 Edgy 32 bit on it.
It seems that every USB 2.0 device is not managed by EHCI but by OCHI instead.
In fact, as soon as I plug a device I get this in dmesg:

[17186599.032000] usb 1-2: new full speed USB device using ohci_hcd and address 7
[17186599.228000] usb 1-2: not running at top speed; connect to a high speed hub
[17186599.240000] usb 1-2: configuration #1 chosen from 1 choice
[17186599.244000] scsi5 : SCSI emulation for USB Mass Storage devices
[17186599.244000] usb-storage: device found at 7
[17186599.244000] usb-storage: waiting for device to settle before scanning
[17186604.244000] usb-storage: device scan complete
[17186604.248000]   Vendor: Sony      Model: Storage Media     Rev: 0100
[17186604.248000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17186604.268000] SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
[17186604.276000] sda: Write Protect is off
[17186604.276000] sda: Mode Sense: 43 00 00 00
[17186604.276000] sda: assuming drive cache: write through
[17186604.300000] SCSI device sda: 2030592 512-byte hdwr sectors (1040 MB)
[17186604.304000] sda: Write Protect is off
[17186604.304000] sda: Mode Sense: 43 00 00 00
[17186604.304000] sda: assuming drive cache: write through
[17186604.304000]  sda: sda1
[17186604.372000] sd 5:0:0:0: Attached scsi removable disk sda
[17186604.372000] sd 5:0:0:0: Attached scsi generic sg0 type 0

Before noting this behaviour,  I have installed this hal substitutes:
[http://www.viciouslime.co.uk/index.php?option=com_content&task=view&id=14&Itemid=33]("http://www.viciouslime.co.uk/index.php?option=com_content&task=view&id=14&Itemid=33")
in order to make my edgy mount my 2g Ipod (as described [here]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068") on launchpad). Therefore, now I downgraded to the Ubuntu original .debs but the behaviour does not change.
Any suggestion?

Thanks.

Usul_

---

### Post by karhulitos on 2007-01-18
Tried too look for an answer for the very same problem. I just bought Western Digital MyBook 250GB and copying data onto it is _very_ slow.

I saw someone fixing similar problem by setting ACPI in BIOS but my Acer 5044 doesn't have such setting in there to test.

[edit]
did what was suggested in this [thread]("http://ubuntuforums.org/showthread.php?t=294938&highlight=running+at+top+speed%3B+connect+to+a+high+speed+hub")
disconnected WD MyBook
```

sudo rmmod ohci_hcd
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd

```
connected WD MyBook back

and video dir copy was 30 minutes against earlier 13h 15min.
Of course this should be automatic for an end user like me but helped me to copy those videos.
I also guess that now I don't have any of my USB1 devices working anymore..

Any help to get USB2 things detected automatically while USB1 things work as designed?

---

### Post by Gustavo Leuck on 2007-01-18
I'm having exactly the same problem. I'll try the solution the guy above posted. But I need my USB1.1 devices working together with the USB2.0. Well, I'll keep searching for the answer... thanks guys :)

---

### Post by karhulitos on 2007-01-20
Anyone, please? Any hints to get both usb1.1 and usb2 running as they should in Ubuntu 6.10?

---

### Post by sysctl on 2007-02-20
Same here. But I've got ehci_hcd and uhci_hcd and the transfer is still slow.

---

### Post by sysctl on 2007-02-20
Remedied by ```
$ sudo rmmod ehci_usb
```...

---

