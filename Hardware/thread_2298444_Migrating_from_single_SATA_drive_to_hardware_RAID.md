---
title: "Migrating from single SATA drive to hardware RAID"
date: 2015-10-11
forum: Hardware
---

### Post by chrisbope on 2015-10-11
I have a Dell Precision T3400 workstation running dual boot Ubuntu Studio 14.04.3 and Mint 17.2 using Grub2 as bootloader on a single 500GB SATA drive connected to the onboard Intel chipset controller. I've installed a Dell PERC 6/i SAS RAID controller and I would like to migrate the whole system from the 500GB SATA drive to boot from a RAID 0 volume on the PERC controller. I know how to setup and configure the RAID, but the question is how can I move a working dual boot system to RAID? Can I use Clonezilla or some other cloning tool to create an image of the working drive and clone it onto the RAID volume?

I've never tried this before, but I think it should be possible. Here are the main hardware specs:

T3400 Precision
Core 2 Q9550 cpu
4GB RAM
Quadro 4000 GPU
One 500GB SATA drive on Intel chipset controller
Dell PERC 6/i SAS RAID controller (installed, no drives connected yet)

I'd rather avoid having to reinstall both OSs from scratch.

---

### Post by oldfred on 2015-10-11
I do not know RAID, nor answer to your question. But RAID zero stripes data across both drives. And then is considered not normally a good choice.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Some who want a gaming only system may use RAID 0, but have ways to backup system regularly or do not care about data.
Often you can get more speed just by adding a SSD.

---

### Post by chrisbope on 2015-10-11
Thanks, but I know all about RAID and different RAID levels. I have been working with RAID for almost 20 years. All my data is backed up to NAS, loss of a RAID0 volume in case of a drive failure is not a problem. SSD is not yet competitive in price/capacity, especially since it would require purchasing new hardware. I do not need to purchase anything to utilize the hardware I currently have.

---

### Post by weatherman2 on 2015-10-11
Assuming it's a hardware RAID card, if you can get two new drives running and build a new array then create new partitions in the array, you can use rsync to copy the existing file system(s) to new partitions.  But you'll want to do that from a live USB or CD boot, unless you are using an LVM so you can make a snapshot of your booted root filesystem before the rsync.  After you copy everything, you'll need to update /etc/fstab in the new root partition to use the new partitions.  Finally, install/update Grub on the array.  I prefer the "chroot" method.

I've only used software RAID 1 (mirror) in Ubuntu so it would be a bit different there.

Perhaps Clonezilla is smart enough to understand a hardware RAID array but probably not RAID 0 - doubt it.

---

