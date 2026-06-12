---
title: "Allocating Hard Drive space using GParted"
date: 2008-06-22
forum: Hardware
---

### Post by Ocean Machine on 2008-06-22
I had another partition where I was running another Linux distro. I decided I hated it, and now want to give that space to the Ubuntu partition. I managed to delete the partition using GParted, but now I can't figure out how to take the Unallocated space and merge it with my Ubuntu partition. I feel as if there's something real simple I'm missing, so any help is appreciated. I've attached a screenshot below:

[IMG]http://i82.photobucket.com/albums/j246/adambargar/Screenshot--dev-sda-GParted.png[/IMG]

---

### Post by mtbsoft on 2008-06-22
It looks to me as if you've just wiped the only primary (and therefore bootable) partition - I don't believe you've left the box in a bootable state (though I could be wrong, I'm still fairly new to Linux myself) - unless you have another bootable drive in there.

I'm not sure you can merge an extended and a primary partition - I think you might have to backup the existing partition, reinstall Ubuntu and restore the copy. 

Alternatively you could reinstall to the unallocated space and copy across (using a live CD) then keep the existing sda6 partition as a /home partition, deleting all else.

Just some ideas for you to research, but please don't do this on just my say-so, wait for some others to confirm.

---

### Post by logos34 on 2008-06-22
Boot the ubutnu live cd and use gparted there.  Grow the extended partition to the front of the disk, then do the same for / sda6.  It will take a good while, though (all the files have to be copied and moved over).  So here's your chance to read War & Peace (well, maybe not THAT long!  Kidding aside it appears that only ~3.3 gbs are used. so it shouldn't be long.  That said, the last time I resized a partition on the left side--~6 gb--it took nearly four hours)

---

### Post by Ocean Machine on 2008-06-23
> **logos34 said:**
> Boot the ubutnu live cd and use gparted there.  Grow the extended partition to the front of the disk, then do the same for / sda6.  It will take a good while, though (all the files have to be copied and moved over).  So here's your chance to read War & Peace (well, maybe not THAT long!  Kidding aside it appears that only ~3.3 gbs are used. so it shouldn't be long.  That said, the last time I resized a partition on the left side--~6 gb--it took nearly four hours)

That worked great! All I had to do was unlock the swap partitions, unmount the Ubuntu partition, and move the sliders. Took just a little over an hour.

Disk Analyzer is showing a completely wrong disk size though. Rescanning didn't seem to help. Anyone know of a way I can get it to "reset"?

---

### Post by logos34 on 2008-06-23
> **Ocean Machine said:**
> That worked great! All I had to do was unlock the swap partitions, unmount the Ubuntu partition, and move the sliders. Took just a little over an hour.

Sounds good.

On second thought, mine took between 3-3 1/2 hrs.  The used space was about double yours, but maybe the fact that it was a heavily-fragmented NFTS partition accounts for the difference.  At any rate, now you know how much longer it can take resizing the left border--if it had been the right side, maybe 5 minutes max.

good luck

add: not sure about disk analyzer discrepancy

---

### Post by mtbsoft on 2008-06-24
Ok, so now I'm very confused!  How come the machine is bootable without a primary partition?  I thought it was necessary to have at least one or is that a Windows restriction.  Could anyone explain this for me, please.

---

### Post by logos34 on 2008-06-24
> **mtbsoft said:**
> How come the machine is bootable without a primary partition?  I thought it was necessary to have at least one or is that a Windows restriction. 

the latter.  Another advantage of linux--you can boot it from practically anywhere. 

(Technically speaking, you cannot install windows on a logical partition unless you make a separate primary boot partition, or there is a prexisting windows installation, which case the installer notes it as the 'active' partition and locates the boot files there.  That said, you can install windows on a primary, then copy an image of it to a logical, but you'd have to edit to edit some boot files and use a bootloader other than ntldr, because the latter will scan the partition table only for primary partitions at startup).

---

### Post by mtbsoft on 2008-06-29
> **logos34 said:**
> the latter. Another advantage of linux--you can boot it from practically anywhere.
Sweeeet! Thanks for the explanation - potentially very useful information for the next time I need to remove Windows from a machine with an existing Linux install.

---

