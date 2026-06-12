---
title: "transfer / and /var directories to new RAID0 array"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Polaris96 on 2009-05-29
I want to transfer my / and /var directories to a RAID0 array.  I'm almost there (if it can actually be done).  here's what I have done, so far, and where I'm hitting the wall:

1.  Installed and addressed 1 PCI-e Adaptec SCSI U320 controller and 2 Seagate Cheetah U320 15k x 18G HDDs
2.  Installed mdadm and lvm2.  Configured and initialized RAID0 array md0 with drives listed above.  set them up in two LVs (md0v and md0r)
3.  used mkfs to install reiser4 FS's on both partitions
4.  used dd to clone my existing / and /var onto md0r and md0v, respectively.

OK, all of that worked GR8.  Not only did I not get errors, but I was able to mount and verify the integrity of the data on the RAID array partitions.  Then:

5.  Altered fstab to mount / and /var onto the new partitions (I used the UUIDs of md0r and md0v)
6.  Rebooted and .... splat!  "filesystem failed integrity check"
7.  used a single user session to restore the original fstab and now things are back to original.

I figured just changing fstab would be a bit of a hack and I'm not surprised it failed.  Is there a way to make the system boot from the Raid directories instead of the original PATA directories of the same name?  The data are identical.  I'm hoping one or more of the following will fix this up:

a)  Maybe either mdadm or lvm have not set up the devices, yet, when fstab tries to mount them?

b)  Maybe there's something in /boot  that can be tweaked to redirect the root directory to it's new location.

I learned a lot getting to this point and even if I need to restart from scratch I'll live with it, but I really hope somebody can help me get past this final hurdle.  

I'm on the pearson retrofit of KDE3.5 for Jaunty, and I don't believe that comes in an alternate install version.  Also, I have read that mdadm is a better solution than fakeraid unless you plan on a dual boot system (I've closed my last window).  I figure there MUST be a way to make this work.  Any help would be much appreciated.

---

### Post by ronparent on 2009-05-29
*a) Maybe either mdadm or lvm have not set up the devices, yet, when fstab tries to mount them?*

Strange, I am having the identicle problem using 9.04 with dmraid (fakeraid). This is a change in behaviour from 8.10 where I was able to mount my raid drives in fstab on boot. I submitted a launchpad bug report on it yesterday when I couldn't resolve the problem after working on it all day. Although I didn't research whether or not the bug happened with mddam, you probably should look into it - your experience looks eriely simular!

---

### Post by Polaris96 on 2009-05-29
It's nice to hear that I didn't set all of this up for nothing.  I'm really happy that, conceptually at least, what I want to do CAN be done.  This kind of flexibility is exactly why I switched to Linux.

That said, may I assume that mounting the cloned partitions in fstab should theoretically work?  I figured maybe something needed to be tweaked in initrd or such so the kernel would boot from the raid array.

---

### Post by Polaris96 on 2009-05-29
oh by the way I am also on an AMD64 phenom 9500 quad.  Asus MVP3A32MVP  wifi NVIDIA chipset.  

I don't like the Asus motherboard - it has been problematic for a year, now. I have intermittent cold start BIOS issues and none of the motherboard USB headers work.  

Although not the main point of this thread, I'm currently shopping for a new home for my phenom and would welcome any advice about motherboards.

---

### Post by ronparent on 2009-05-29
You remind me that I will have to update my footer - the hardaware is fine but I am obviously using jaunty. I also am shopping MBs. This has been a secondary system since I had to rma the Asus board - now mostly minor glitches but disenchanting. The nvidia nforce 3 chip sets on both my MBs is dated anyways. Writing on wall - updated nvidia windows drivers are not available. The win7 provided drivers don't recognize my raid0 array (surprising the raid1 array on my other tower work fine). I will probably replace soon with an AMD quad core compatible board. It will probably be msi or gigabyte. Haven't decided yet whether am2+ or am3. 

On this topic I am sure you could get tons of advise/opinion. But not likely here. Not too many people will look at a post on raid0.

---

### Post by Polaris96 on 2009-05-29
I have looked at gigabyte and msi, also.  I'm sticking with AM2+ b/c my Phenom is still pretty new and the DDR2's also only a year old.  The gigabyte board is nice but the reviews I read say it's cluttered when you plug in a few PCI cards - the pci-e16 slots occult the pci-e4 and pci-ei slot.  I like SCSI peripherals, so, until someone makes a m/b with native SCSI support I need real estate on the PCI bus.  

The msi looks robust but I can't find any reviews on it, yet.  I've also been checking out Biostar.  Their stuff looks pretty good, as well, even though it's not super cutting edge.  Since I'm looking for an AM2+, anyway, that deosn't bother me much.

Regarding the Raid issues we've been having, I'm going to try altering the boot device in grub to reflect the Raid array.  I'll let you know if it works.

---

### Post by ronparent on 2009-05-29
I've seen some reference to mod and recompile the initrd to try to assure mddam gets started before fstab gets loaded. But I am not deep enough into linux to attempt anything like that myself at this point. I'm a bit sceptical that altering boot devices in grub will help any. Maybe for a raid1 setup.

Newegg customer reviews are somewhat helpful. You do have to take them with a grain of salt since the customer is ofen overboard patting themselves on the back for a brilliant selection or totaly bummed out if things didn't work right. Some of the reviews are  thoughtful and informative though.

---

