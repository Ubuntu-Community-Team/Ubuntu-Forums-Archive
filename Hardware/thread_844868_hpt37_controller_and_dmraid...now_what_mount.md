---
title: "hpt37 controller and dmraid...now what? mount?"
date: 2008-06-30
forum: Hardware
---

### Post by RobN on 2008-06-30
I've got an old computer I'm setting up ubuntu on, so it can be the kid's PC and a network storage location. It previously had a RAID0 striped set on it, with an hpt370 controller on the motherboard -- and since it previously had XP, the partition is an NTFS partition.

Now I copied most everything across the network, before I pulled the main drive out (the XP drive was not part of the array) and put it in a new PC, but I've found there are files on this array I still need. So before I pull the disks out of the array and reformat them as standard IDE drives in ubuntu, I need to mount it again. Read-only would be fine.

I figured out I needed dmraid -- installed it from Synaptic, and it seems to see the array:

```
sudo dmraid -s
*** Active Set
name   : hpt37x_ccdjjfgdff
size   : 536870400
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0


sudo dmraid -ay
RAID set "hpt37x_ccdjjfgdff" already active
RAID set "hpt37x_ccdjjfgdff1" already active

```
But...what now? All the guides I see assume you want to use the RAID array as a boot partition -- I don't care about that, as I have a separate drive that ubuntu is installed on. They also assume you already know how to mount it, which I don't. So...help!

The closest I've been is this:
```
sudo mkdir raid
sudo mount -tnfs /dev/mapper/hpt37x_ccdjjfgdff /mnt/raid
mount: wrong fs type, bad option, bad superblock on /dev/mapper/hpt37x_ccdjjfgdff,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I understand I need to mount it, but I'm not sure how to get it to work -- I've dabbled in ubuntu on my laptop before, but didn't have to mount much manually, as the setup found and took care of it for me. Where to from here, exactly?

---

### Post by Odrodzona-Sarmacja on 2008-06-30
For auto mounting in Ubuntu you need to look into "/etc/fstab".

---

### Post by RobN on 2008-06-30
I don't care about automounting, unless that would be easier to set up. I can't manually mount the thing, so I assumed automounting would be harder.

If I can mount it, I can copy files off over the network and be done with it. But I can't mount it. It's as though even with dmraid, ubuntu still sees them as two separate disks, instead of seeing them as one combined volume.

I tried installing gparted -- it sees the partition on each drive, and recognizes it as NTFS, but then says "Unable to read the contents of this filesystem! Because of this some operations may be unavailable." Well, I don't want to reformat it, just mount it...so I'm probably looking in the wrong place.

---

### Post by Ptero-4 on 2008-06-30
RobN. the command is
```
sudo mount **-t ntfs** /dev/mapper/hpt37x_ccdjjfgdff /mnt/raid
```

---

### Post by RobN on 2008-07-08
> **Ptero-4 said:**
> RobN. the command is
```
sudo mount **-t ntfs** /dev/mapper/hpt37x_ccdjjfgdff /mnt/raid
```
Thank you -- that finally did it.

I lost track of know how many different combinations I tried that did NOT work, but that one (well, one slightly different, in that it was the "other" entry in /dev/mapper that finally worked) was the right combination.

Awesome. My wife and I thank you!!

---

### Post by aminalid on 2008-10-10
> **Ptero-4 said:**
> RobN. the command is
```
sudo mount **-t ntfs** /dev/mapper/hpt37x_ccdjjfgdff /mnt/raid
```

Worked for me too... but only after adding the number of the partition:
```

sudo mount -t ntfs /dev/mapper/nvidia_ibdeebgj**1** /mnt/raid

```
nvidia_ibdeebgj**1** is my C: drive on windows.

Thanks.

---

### Post by Willberto on 2009-01-28
I am pretty much in the same situation as the original poster but I am still having a problem.  Probably due to the fact that the RAID itself is split into a couple partitions.  When I give the command givin by Ptero-4 

```

NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_bcfcaddj': Invalid argument
The device '/dev/mapper/nvidia_bcfcaddj' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the [B]whole disk instead of a
partition[/B] (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

How do I specify a particular partition?

EDIT:  Got it to work.

---

