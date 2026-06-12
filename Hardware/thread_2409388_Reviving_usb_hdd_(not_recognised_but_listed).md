---
title: "Reviving usb hdd (not recognised but listed)"
date: 2019-01-01
forum: Hardware
---

### Post by porkpiehat2 on 2019-01-01
Hi all,

I'm trying to revive an WD My Passport Ultra 1TB usb hard drive that functioned well until recently. Currently, it is listed under 'lsusb' but the device won't show under 'fdisk'.

The background: I tried to BitLocker-encrypt the driver on a Windows 7 64-bit machine. Halfway through, the drive became unresponsive and the process halted. Since then, I could not access the drive anymore from Windows.
I had mild success on an old Ubuntu 16.4 laptop - the drive was listed under 'fdisk' but not accessible. I first attempted a format ('mkfsdos -F 32 -I /dev/sdb'), but that was stuck for over an hour with no output, not even that it started nor any warnings. I interrupted the formatting and tried restoring the disk after with mkusb. This seemed hopeful, but at the end it said it failed and I should re-plug the drive. Since then, the drive is no longer recognised.

Below is the output of dmesg when I plug in the drive. The read/64, error -71 I searched already, but no luck there. Did the drive just crash, or did I screw up the readability of the drive contents in  my attempts to revive it? There's no important data on it, but if possible I would like to re-use the drive.

Any help is surely appreciated!

```
[ 1774.144139] usb 2-3: new high-speed USB device number 6 using ehci-pci[ 1774.768141] usb 2-3: device descriptor read/64, error -71
[ 1775.033232] usb 2-3: New USB device found, idVendor=1058, idProduct=0810
[ 1775.033237] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1775.033241] usb 2-3: Product: My Passport 0810
[ 1775.033244] usb 2-3: Manufacturer: Western Digital
[ 1775.033248] usb 2-3: SerialNumber: 575831314538335248353437
[ 1775.033668] usb-storage 2-3:1.0: USB Mass Storage device detected
[ 1775.035333] scsi host6: usb-storage 2-3:1.0
[ 1776.065087] scsi 6:0:0:0: Direct-Access     WD       My Passport 0810 1042 PQ: 0 ANSI: 6
[ 1776.065683] scsi 6:0:0:1: Enclosure         WD       SES Device       1042 PQ: 0 ANSI: 6
[ 1776.069874] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1776.070131] ses 6:0:0:1: Attached Enclosure device
[ 1776.070331] ses 6:0:0:1: Attached scsi generic sg3 type 13
[ 1807.468076] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1807.624912] ses 6:0:0:1: Failed to get diagnostic page 0x1
[ 1807.624917] ses 6:0:0:1: Failed to bind enclosure -19
[ 1838.188090] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1870.956077] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1903.724069] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1936.492082] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1936.648899] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK
[ 1936.648901] sd 6:0:0:0: [sdb] Sense not available.
[ 1936.648906] sd 6:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[ 1936.648908] sd 6:0:0:0: [sdb] 0-byte physical blocks
[ 1967.212066] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 1967.368914] sd 6:0:0:0: [sdb] Write Protect is off
[ 1967.368917] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 1999.980049] usb 2-3: reset high-speed USB device number 6 using ehci-pci
[ 2000.136886] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2000.136891] sd 6:0:0:0: [sdb] Assuming drive cache: write through
```

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]porkpiehat2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2107974"),

Can you see the drive in gparted?

---

### Post by mikasu on 2019-01-02
Hi
Just mentioning, it's possible that the disc drive system utility see it if gparted doesn't. Just that the system utility is a bit more basic in partitioning.

---

### Post by porkpiehat2 on 2019-01-02
> **clementc said:**
> Hi [**[COLOR=#000000]porkpiehat2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2107974"),

Can you see the drive in gparted?
If I remember correctly, the drive was not listed by GParted - otherwise I would have chosen that route rather than command line formatting. It did, however, show up in Disks before.

---

### Post by clementc on 2019-01-02
Hi [**porkpiehat2**]("https://ubuntuforums.org/member.php?u=2107974"),

Just for clarity sake, can you please check again using gparted first then disks and try to format the drive through these utilities?

I am sorry if you have already tried this, I simply want to make sure we are not missing anything.

---

### Post by porkpiehat2 on 2019-01-02
I will double-check GParted tonight. As stated in the opening post, it is *not* listed under Disks anymore, but it was before my 'mkusb'-attempt.
In addition: I can feel the drive spinning and I don't hear any odd sounds that could indicate mechanical failure.

---

### Post by mikasu on 2019-01-02
Sounds silly but have you tried re-plugging it in?

---

### Post by porkpiehat2 on 2019-01-02
@mikasu: yes, I've tried re-plugging it, other computers etc. None worked.

Strangely, this afternoon it suddenly worked partially on a Win 10 laptop. Windows recognised it and the BitLocker-process froze when trying to unlock the drive. To me this indicates that either the BitLocker-partition is faulty (since it stopped mid-encryption), or the disk is physically damaged anyway. The WD Utility was also unable to do anything with it.

Und my Ubuntu laptop it showed again in GParted. I'm attempting to delete the partition and format it again, but GParted went grey at '2 operations pending' and is like this for more than 20 minutes already (drive is spinning though). I'll leave it overnight and see if it does anything.

---

### Post by clementc on 2019-01-02
Hi [**porkpiehat2**]("https://ubuntuforums.org/member.php?u=2107974"),

Although the drive might not have suffered physically from the failed encryption, it looks like it is now in a state where most tools can't do anything with it (kind of a soft lock).

If it is still under warranty, I would recommend that you send it back to the store where you purchased it and ask for a replacement.

You have tried a lot of things already, and except maybe trying a low level tool on it (like dd), I am not sure what else can be done about it.

As a last resort (if gparted fails), you could try the following command to run:

dd if=/dev/zero of=/dev/sdX bs=1M (replace X with the target drive letter)

Warning: this will wipe the entire drive specified by the of= parameter.

---

### Post by porkpiehat2 on 2019-01-03
Thanks for the reply, clementc.

GParted indeed failed - it was still stuck this morning, and did not respond again until I unplugged the drive. Then it gave me an obvious read/write-error. The drive is no longer under warranty unfortunately, otherwise I would have brought it in right away.

I thought mkusb was also quite low level? I've seen the DD trick often too, that was also on my list to try. Will attempt that tonight. To be sure, I will leave the disk in for ~10 minutes before attempting this.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]porkpiehat2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2107974"),

I am sorry to hear that gparted failed last night. Hopefully dd will be able to resolve your issue.

Have a nice day and good luck with your drive.

---

### Post by Yellow Pasque on 2019-01-03
I would try creating a new partition table in gparted instead of trying to delete partitions (warning: you lose all data on the drive).

---

### Post by mikasu on 2019-01-04
The problem is: the drive isn't there in gparted. It's simple presence in the system would freeze gparted until the drive is unplugged as he said earlier.

---

### Post by porkpiehat2 on 2019-02-22
After some time I did a new attempt this morning on my old laptop, after upgrading it to Ubuntu 18.04. The drive was briefly visible and I attempted to reset the partition table with fdisk, but that timed out. After that, the drive was not recognised again.
I followed syslog when plugging in the drive and some time after that (*tail -f /var/syslog | grep usb*). The log shows a read error *'read/64 error -71'*, of which I can find very little information. But that is not the most troublesome part I think. I think the constant resetting and the subsequent timeout are worse, and I think that I can safely conclude that there is at least something wrong with the drive controller, possibly also with the drive itself (although it spins just fine).

If someone still has a trick to revive it though, I'm still willing to try some options :)

```
Feb 22 09:02:53 paul-HP kernel: [ 1099.312138] usb 2-1: new high-speed USB device number 4 using ehci-pciFeb 22 09:02:54 paul-HP kernel: [ 1099.936060] usb 2-1: device descriptor read/64, error -71
Feb 22 09:02:54 paul-HP colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
Feb 22 09:02:54 paul-HP kernel: [ 1100.208376] usb 2-1: New USB device found, idVendor=1058, idProduct=0810
Feb 22 09:02:54 paul-HP kernel: [ 1100.208381] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 22 09:02:54 paul-HP kernel: [ 1100.208385] usb 2-1: Product: My Passport 0810
Feb 22 09:02:54 paul-HP kernel: [ 1100.208388] usb 2-1: Manufacturer: Western Digital
Feb 22 09:02:54 paul-HP kernel: [ 1100.208392] usb 2-1: SerialNumber: 575831314538335248353437
Feb 22 09:02:54 paul-HP kernel: [ 1100.209495] usb-storage 2-1:1.0: USB Mass Storage device detected
Feb 22 09:02:54 paul-HP kernel: [ 1100.217018] scsi host6: usb-storage 2-1:1.0
Feb 22 09:02:54 paul-HP mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1"
Feb 22 09:02:54 paul-HP upowerd[1417]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0
Feb 22 09:02:54 paul-HP upowerd[1417]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1
Feb 22 09:02:59 paul-HP colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
Feb 22 09:03:28 paul-HP kernel: [ 1133.676049] usb 2-1: reset high-speed USB device number 4 using ehci-pci
Feb 22 09:04:00 paul-HP kernel: [ 1166.444049] usb 2-1: reset high-speed USB device number 4 using ehci-pci
Feb 22 09:04:31 paul-HP kernel: [ 1197.164048] usb 2-1: reset high-speed USB device number 4 using ehci-pci
Feb 22 09:05:04 paul-HP kernel: [ 1229.932337] usb 2-1: reset high-speed USB device number 4 using ehci-pci
Feb 22 09:05:37 paul-HP kernel: [ 1262.700045] usb 2-1: reset high-speed USB device number 4 using ehci-pci
Feb 22 09:07:41 paul-HP systemd-udevd[285]: seq 3488 '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/host6/target6:0:0/6:0:0:0/block/sdb' is taking a long time
Feb 22 09:07:46 paul-HP kernel: [ 1391.724024] usb 2-1: reset high-speed USB device number 4 using ehci-pci


```

---

### Post by tea for one on 2019-02-22
> **porkpiehat2 said:**
> If someone still has a trick to revive it though, I'm still willing to try some options :)

Just a shot in the dark, but the following website has some advanced tools and information which may help revive the disk.

The utilities gdisk and fixparts would be worth a look.

[http://www.rodsbooks.com/](http://www.rodsbooks.com/)

Good luck

---

