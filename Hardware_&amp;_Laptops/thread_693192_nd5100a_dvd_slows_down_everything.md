---
title: "nd5100a dvd slows down everything"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by mzembe on 2008-02-10
I was copying a pile of rar archives from the dvd on my laptop and it brought my computer to it's knees. The web browser would gray out on and off, it took several minutes to fire up the system monitor... I moused over firefox on the start panel and had to wait forever for the preview bubble and the right click and the close. It never closed.... Much later the files were finally copied:popcorn: and I had my system back, but it like a horrible flashback to windows or something. 
I wonder what that was all about, this thing has a 82801FBM chipset that is supposedly SATA although the hard drive is a 7K100 PATA type, the cdrom is a nd5100a removable(PATA I believe). Gutsy likes to pretend they are scsi devices, hdparm reports 16bit IO and won't change that kind of stuff as they are. I was thinking maybe I could disable DMA on the cdrom but you would think the drive would just copy slowly without interfering with the responsiveness of the rest of the system. 
I'm running the stock kernel (the one with the scary userland [exploit]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/190587"))  . 
Maybe I should try to somehow force these drives to behave like ATA devices and hdparm them into submission. How is this accomplished? I'm guessing I might change the root device in GRUB to reflect /dev/hda6 and the fstab.. Does anybody else have this problem?

---

