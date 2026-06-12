---
title: "Partitioning demystified and help cloning system"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by sisyphus1978 on 2009-09-03
Hi. 

Hope you fine folk can help. I have successfully set up a clonezilla pxe machine, and I've been using it for a couple of months. The machine itself has two HDD. Fdisk -l gives this:

> Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd435d435

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14916   119812738+  8e  Linux LVM
/dev/sda2           14917       14946      240975    5  Extended
/dev/sda5           14917       14946      240943+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f6e52d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
First question. Have I set this up incorrectly? All I want the machine for is to backup and store/restore the clonezilla images I have created. 

Second question. I want to clone the first HDD to the second, so that if the first dies, I can swap it in (and I don't have to set it up again). I was going to DD the first to the second, but the partitioning of the first HDD is confusing me.

Any help gratefully received.

---

### Post by stlsaint on 2009-09-03
are you asking for raid1 setup or simple cloning. Repos should have a few options for cloning. not at my rig now so i cant check. but do check repos before going off archive.

---

### Post by sisyphus1978 on 2009-09-03
What I am asking is actually very simple (probably). I thought I had two 120gb drives. I was going to DD clone the one that is set up as a clonezilla machine (it already works great) onto the other HDD, so that if the 1st one dies, I have a backup (and don't have to set it all up again).  Then I looked at the fdisk info and didn't really get what I had done to it. I hoped somebody could explain.

---

### Post by stlsaint on 2009-09-03
see [here]("http://ubuntuforums.org/showthread.php?t=135172").

please mark thread as solved if this is what you need.

---

### Post by Penguin Guy on 2009-09-03
> **sisyphus1978 said:**
> Have I set this up incorrectly?
You've put one of your /dev/sda partitions inside an extended partition; this has no negative effect but does make things a little more confusing. You should also consider using [RAID]("http://www.google.co.uk/search?q=RAID") rather than simply copying the partition.

I can't help you any further with the partitioning unless you can tell me which partition clonezilla is on.

> **sisyphus1978 said:**
> Disk /dev/sda: **122.9 GB**
Most HDDs have a whole number of gigabytes. Be suspicious.

---

### Post by sisyphus1978 on 2009-09-03
stlsaint: Thanks for the link.

Penguin Guy: Okay, that's helpful. I feel like I'm almost understanding it.

So I've attached a screendump from Gparted. I think clonezilla and ubuntu are on sda5, which, if I'm right, means that sda1 is not even being used.
I guess what I want is to mount sda1 so that the clonezilla images can reside on that part of the disk too.

So. Can I grow sda2 (sda5) into sda 1. Or am I better off cloning sda5 onto the other disk and then copying back?

I am beginning to love linux. Slowly.

---

### Post by sisyphus1978 on 2009-09-04
I'm providing some more details about the various disks/partitions. If somebody could help shine a light on all this, I'd be very grateful.

Recap: I essentially want sda and sdb to be identical copies. I would like full capacity of both drives to be accessible to the clonezilla partition.
----------------------------

/dev/mapper/ubuntu-root        (113.01 GiB)
/dev/mapper/ubuntu-swap_1    (1.24 GiB)
/dev/sda            (114.49 GiB)
/dev/sdb            (111.79 GiB)

---

### Post by sisyphus1978 on 2009-09-04
Can anyone tell me if deleting sda1 will result in me losing data?

---

### Post by sisyphus1978 on 2009-09-04
...

---

### Post by sisyphus1978 on 2009-09-04
Okay. This is still confusing me. Here's my fstab:

> # Entry for /dev/mapper/ubuntu-root :
UUID=8aaaade5-3b89-482f-9ad7-a32cb1c40016 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=20ab1fa3-bebf-4153-b44f-aacf15320cb9 /boot ext2 relatime 0 2
# Entry for /dev/mapper/ubuntu-swap_1 :
UUID=f4dd9d3a-87f5-4c83-8045-40270d052219 none swap sw 0 0
# Entry for /dev/sdb1 :
UUID=e917ce08-8524-4cb1-99a9-758d23c8ce7c /media/store ext2 defaults 0 0
And. If you check out the screen-dump, what the heck is sdc1?

Like I say, I am flummoxed. I would like to get it sorted without destroying any functionality...

---

### Post by sisyphus1978 on 2009-09-05
...

---

### Post by sisyphus1978 on 2009-09-05
...

---

### Post by sisyphus1978 on 2009-09-06
...

---

### Post by sisyphus1978 on 2009-09-06
Please somebody explain the partitioning to me. You can give a man a fish. He eats for a day. Explain how to fish. He never comes back to annoy you (but drowns in a fishing accident).

---

### Post by sisyphus1978 on 2009-09-07
I just booted up a live-cd. I can mount a 245.7MB disk which shows grub etc. However I used it this morning and I know it has some clonezilla imgs on it (40 gig at least).

Please can somebody who understands explain what is going on. Please.

---

### Post by sisyphus1978 on 2009-09-07
How do I get some help around here?

---

### Post by sisyphus1978 on 2009-09-07
Am I in the wrong forum or what?

---

