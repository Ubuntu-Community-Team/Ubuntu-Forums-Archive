---
title: "Changin partition types"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by ahpitre on 2009-05-20
Hello,
 

I have an HP laptop, with 4 primary partitions. These are, in order : 
[LIST]
[*]Windows Vista is the 1st partition
[*]Windows Recovery (partition allows to run HP recovery software)
[*]LINUX EXT partition (where Ubuntu 9 is installed)
[*]LINUX Swap partition
[/LIST]There are 2 unallocated regions in the Hard Disk. I want to create an additional NTFS partition, using this space. Idea is to use it to store my documents and data. I am not able to do this as the software (Paragon Partition Manager 10 Personal) displays error that no more partitions can be made). Found out that 4 primary partitions is the max. 1 Hard Disk can hold.
 
Can I change the LINUX partition to an Extended partition, then add 1 logical partition to this Extended partition, and then change/move the SWAP partition to the logical drive within the Extended partition? If I do this, will LINUX work, or will it fail to boot, and if so, can this be corrected (using GRUB or any other tool), so it can be made bootable again? 
 
PS : I am using GAG 4.10 Boot loader, installed in the MBR. GAG allows booting to Windows, or to LINUX (Via GRUB installed on LINUX partition).

---

### Post by brentrubeck on 2009-05-21
You're pretty much on the right track.  You need to delete the swap partition, and create an extended partition.  Inside an extended partition you can have a lot more than 4 partitions so you would able to create a new swap partition and your NTFS partition for sharing files.  There is a technical reason for only having 4 primary partitions and I think it has to do with the size of the boot sector on the disc.  After you create an extended partition that limitation goes away.  Also when you boot up to linux it should look at the partition table on the disc and find the linux swap space.  Additionally if you boot up to your ubuntu CD you should be able to use gparted to edit your drive, if your other software is giving you problems.

---

### Post by ahpitre on 2009-05-21
If I delete only the swap partition, then create an extended. In the extended I can create a new Swap partition, and the other data partitions. Do you think that LINUX will boot up, or will it have problems because the swap partition has been changed? Thanks for your help.

---

### Post by TAFKARS on 2009-05-21
> **ahpitre said:**
> If I delete only the swap partition, then create an extended. In the extended I can create a new Swap partition, and the other data partitions. Do you think that LINUX will boot up, or will it have problems because the swap partition has been changed? Thanks for your help.

I had exactly the same problem. I have just booted from a live cd (8.04) in order to access an 'unlockable' gparted. I actually needed to select the option swapoff rather than unmount as unmount still remained greyed out. swapoff removed the key icon and I was then free to delete the swap partition. I then created an extended partition from the remaining unused space, and in this new partition created a new (logical) partition for the swap.

Quite straightforward, and does not appear to have interrupted the boot process (although upon rebooting I observed some text rather than the 'loading bar' - as if booting from a CLI). Not sure if this is significant as I am quite new to all this.

Hope this helps.

---

