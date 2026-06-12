---
title: "Cloning root partition to new SSD"
date: 2009-08-18
forum: Hardware
---

### Post by kubuntuuser on 2009-08-18
Hi Experts,
I'm hoping someone can help me out cloning my root partition to a my new crucial 64 GB SSD. 

I currently have a 1TB SATAII hard drive split up as follows
[LIST]
[*]/     = 30 gig  (ext3)
[*]swap  = 4 gig   
[*]/home = everything else 700+ gig (ext3)
[/LIST]

I'd prefer not to re-install Ubuntu and was hoping to clone my root partition using Clonezilla and put this on the new SSD. As far as I'm aware, this is the easy bit.

However I have a number of questions regarding the processes after the partition has been cloned and placed on the SSD and more general questions about maximising the life out of my new SSD. 

I can imagine that a number of files will need to be updated to ensure that /home is still mounted at boot and that the new / partition becomes the partition that is booted from instead of the old root partition. I'm thinking the grub.conf and /etc/fstab are the likely files that would need to be updated?

Is this assumption correct or will other files need updating too? Can anyone provide an example of the types of changes that would be required? 

To ensure that I maximize the life of my SSD I've heard that you should use an non-journalling filesystem like ext-2 to prevent re-writes to the same area of the disk thus shortening the life of an SSD? How true is this, does it really matter if I leave it mounted as ext3 which is how it will be cloned?

I'm not too concerned with journalling the root partition as long as the /home partition where my data is stored continues to be journalled as this is where I'm worried about data corruption. 

I'd also like to create a dedicated /var partition for log files (again to increase the life of my SSD) back on the SATA drive in the place of the old root partition. Does anyone have any recommendations on sizes? Also what will I need to do to ensure that this new partition is mounted at boot? How do I reclaim the space used by the original var area that would be taken up by the old var area

I know there is a lot of questions in this post but would appreciate any help to make this as pain-free as possible.

Thanks in advance guys

---

### Post by djurny on 2009-08-18
> **kubuntuuser said:**
> To ensure that I maximize the life of my SSD I've heard that you should use an non-journalling filesystem like ext-2 to prevent re-writes to the same area of the disk thus shortening the life of an SSD? How true is this, does it really matter if I leave it mounted as ext3 which is how it will be cloned?
life-cycle of nandflash depends on how many times a block/page is read and/or written.. it is a common misconception that it only will wear with write actions.. using an ssd i would assume that the wear-levelling and bad-block remapping stuff is handled by the ssd firmware and is totally filesystem ignorant..
if you are using bare nandflash, which is not the case with ssds, then you should start worrying about filesystems.. jffs2 and ubifs are two of the many nandflash specific filesystems out there and never should you use a filesystem without wear-levelling and/or bad-block remapping on a bare nandflash device..! (unless you don't care about data retention ;-))

> **kubuntuuser said:**
> I'm not too concerned with journalling the root partition as long as the /home partition where my data is stored continues to be journalled as this is where I'm worried about data corruption. 
journalling only arranges disk writes into bulk transactions with the ability to roll-back the last transaction.. the only time when you need to start worrying about data corruption is when you do not sync/unmount filesystems cleanly or when you have intermittent power failures..

---

