---
title: "Quickest way to wipe a hard drive?"
date: 2010-04-26
forum: Hardware
---

### Post by x-shaney-x on 2010-04-26
I'm preparing to install lucid (as well as trying some other distros) but before I do I want to wipe out my drive.
Over time I have done a lot of messing around with partitions.  Deleting, resizing etc and I have noticed it has gotten out of hand with way too many partitions than I need as well as little bits of unallocated space that are to small to be any use.
So I have decided to wipe everything out and start again but what is the quickest way?
The drive is a claimed 300GB (gparted reports it at 280GB)

Criteria:
1.  I want it to be quick
2.  I want something I can just run from a live cd

I did try dd to zero the drive but after leaving it overnight it still wasn't finished so I cancelled it to try something else.

I'm not talking about multi-pass secure erasing here, just something to basically put it to the state of a new drive.

Thanks in advance.

---

### Post by Grenage on 2010-04-26
If you just want it cleared, simply repartition and format it.  You could use Gparted from a live CD.

It's reported as 280GB because that's what it really is.  Manufacturers rate them as if 1000 bytes in a MB, 1000 MB in a GB, instead of 1024 (someone will probably correct me with a more technically correct explanation).

---

### Post by x-shaney-x on 2010-04-26
I did try that method before on another drive and I was unable to install win98 (yes that long ago) because of supposed data it couldn't read.
And the last time I did it on THIS drive, after rebooting it brought up the grub loader (nothing to load but still brought it up) so that method clearly leaves something there.

---

### Post by prshah on 2010-04-26
> **x-shaney-x said:**
> 
Criteria:
1.  I want it to be quick
2.  I want something I can just run from a live cd

Standard Disclaimer: THESE ARE VERY DANGEROUS COMMANDS; DO NOT TRY THEM AS AN EXPERIMENT. THE FOLLOWING ACTIONS ARE PERFORMED BY PROFESSIONALS; DO NOT ATTEMPT TO IMITATE THEIR ACTIONS.

Quick wipe-out, from live CD, HDD unmounted (including swap partitions)```
sudo swapoff -a
sudo dd if=/dev/zero of=/dev/sda bs=600 count=1
``` This will instantly wipe out all partition and boot (mbr) information.

For a more through wipe, to avoid possibility of recovery```
sudo dd if=/dev/zero of=/dev/sda bs=32k
``` note the blocksize parameter; this will speed things up considerably (no need overnight). However, it will still run for several hours, and it should be done twice/thrice for maximum effectiveness.

/dev/sda is an example, please replace with a suitable drive name as in your case.

PLEASE DO NOT USE THESE COMMANDS FOR NEFARIOUS PURPOSES.

---

