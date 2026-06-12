---
title: "Cannot mount any type of media cards"
date: 2008-12-06
forum: Hardware
---

### Post by Eoin087 on 2008-12-06
Hi I'm hoping somebody here will be able to help me.

I can't mount any type of media cards with my external card reader. The card reader itself is showing up in "Computer" but when I try to mount, lets just say a memory stick, it says "Unable to mount location - Can't mount file". This happens with whatever type of card I try.

Is there anyway to fix this? I'm still fairly new to ubuntu and wouldn't have the "know how" about what steps I should take.

I'm using ubuntu 8.04 hardy and the card reader is a Hama 8-in-1.

I've searched the forum for something similar to this problem with no luck, so any help would be greatly appreciated. :)

---

### Post by taurus on 2008-12-06
Open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Eoin087 on 2008-12-06
Thanks for replying
Here's the result of the command.
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6        5040    40443637+   7  HPFS/NTFS
/dev/sdb3            9121        9726     4867695   db  CP/M / CTOS / ...
/dev/sdb4            5041        9120    32772600    f  W95 Ext'd (LBA)
/dev/sdb5   *        5041        8865    30724281   83  Linux
/dev/sdb6            8866        9120     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by taurus on 2008-12-06
I assume you have plugged in a card, right?  Otherwise, plug one in and post

```
dmesg | tail
sudo fdisk -l
```

---

### Post by Eoin087 on 2008-12-06
> **taurus said:**
> I assume you have plugged in a card, right?  Otherwise, plug one in and post

```
dmesg | tail
sudo fdisk -l
```
Yeah I had a card plugged in.

This is from the dmesg
```
[ 7473.556026] sd 5:0:0:3: [sdf] Unsupported sector size 1.
[ 7473.556032] sd 5:0:0:3: [sdf] 0 512-byte hardware sectors (0 MB)
[ 7473.558028] sd 5:0:0:3: [sdf] Write Protect is on
[ 7473.558035] sd 5:0:0:3: [sdf] Mode Sense: 03 00 80 00
[ 7473.558038] sd 5:0:0:3: [sdf] Assuming drive cache: write through
[18047.696028] cdrom: This disc doesn't have any tracks I recognize!
[18402.463865] cdrom: This disc doesn't have any tracks I recognize!
[18877.162498] UDF-fs: No VRS found
[18877.191689] ISO 9660 Extensions: Microsoft Joliet Level 3
[18877.224890] ISO 9660 Extensions: RRIP_1991A
```

The fdisk command results remain the same as above :S

---

### Post by Eoin087 on 2008-12-06
After installing intrepid, the card reader still shows in "Computer", but gives a little more information when I attempt to mount it.
```
Unable to mount location
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Anybody know what this means? And is there a way around it?

---

### Post by Eoin087 on 2008-12-07
Anybody?

---

### Post by tsl on 2009-04-12
What solved the issue for me has been:

1. Purge policykit (please note that this will remove ubuntu-desktop as well) from Synaptics
2. As Ubuntu-desktop has been removed I had to manually reconnect to the LAN (the network manager applet has been removed as well)
3. Reinstall ubuntu-desktop
4. Reboot the machine

---

