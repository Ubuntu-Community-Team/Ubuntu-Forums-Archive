---
title: "is my HDD dead?"
date: 2010-04-06
forum: Hardware
---

### Post by LastWho on 2010-04-06
hi,
i am trying to connect an HDD (IDE 250 Gb), to my laptop, by using an "USB to IDE adapter"..
The HDD unlike other USB drives or my phone, doesn't mount directly

Gparted doesn't show the HDD and here is what i get after plugging in it: 

dmesg: 
```


[ 1278.808132] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 1279.014245] usb 1-1: configuration #1 chosen from 1 choice
[ 1279.064278] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1279.069026] usb-storage: device found at 6
[ 1279.069036] usb-storage: waiting for device to settle before scanning
[ 1284.070985] usb-storage: device scan complete
[ 1289.718102] usb 1-1: USB disconnect, address 6
[ 1289.724200] scsi 6:0:0:0: Device offlined - not ready after error recovery

```

lsusb: 
```
 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 05e3:0702 [COLOR="DarkRed"]Genesys Logic, Inc. USB 2.0 IDE Adapter[/COLOR]
Bus 001 Device 004: ID 064e:a103 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


sudo fdisk -l

```
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e32ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris
```

is there a way to tell for sure whether my HDD is damaged or not!
thanks in advance

---

### Post by byStanderone on 2010-04-06
...hard to say if it's the hdd that's at fault, could also be the hardware interface configuration in your system. since the hdd is external, perhaps you can test it on another box if availability permits.

---

### Post by LastWho on 2010-04-06
hmmm that's my pb, i am not at home so i can't test it on my pc, but it was working fine the last time i used it .. (windows xp ntfs on it)

---

### Post by byStanderone on 2010-04-06
...aha, so it is in ntfs, findout if your have ntfsprogs installed, that's a needed piece for ntfs job.

---

### Post by LastWho on 2010-04-07
i just tested it on another pc (windows xp) and i think it is really damaged :(
thanks

---

### Post by doas777 on 2010-04-07
> **LastWho said:**
> i just tested it on another pc (windows xp) and i think it is really damaged :(
thanks
install speedfan on the XP box, and go to the tab that says S.M.A.R.T.
have it run a smart test on the drive to see how it is physically. then if it tests ok, use chkdsk to make sure the filesystem is fine. I try to never mount my ntfs drives while in linux, as it is just hard to keep ntfs healthy when the primary OS can't establish it's health, or repair it when needed. I find my fileserver beats a shared drive anyway.

---

