---
title: "disk upgrade for dual boot dual disk"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Michael Matthews on 2009-07-06
I was running dual disk dual boot Ubuntu 8.4 and vista. Decided to upgrade my disk drive as disk was getting tight(Vista side). I have been long history of multi boot and partitioning reflected legacy issues like have all boot partitions on one drive so I wanted to clean that up. One disk for vista, one for ubuntu. I had done this in the past but it was very messy on the windows side. This time I did a little research to try and do it right.

Basically had 4 active partitons:
hd0: Vista C:,Ubuntu root
hd1: Vista D:,Ubuntu home (data I have kept for many years) , Extra Ubuntu partition.

All drives were SATA. Hooked new drive up to system.

1) move ubuntu root fs to second drive. Luckily, I had an extra partition on second drive with adequate space for Ubuntu system which makes this much easier. Everything is done as sudo obviously.
> cd /
> cp -ax * /<spare partition>

Edited grub/menu.lst to option both boot partition.
> grub-install /dev/sda
> grub-install /dev/sdb

Edited /etc/fstab on new partition to mount correct root. Used blk_id to determine UUID stuff. Other commands are vol_id,tune2fs -l,udevinfo

Verified that booting ubuntu from new partition worked.

2) Now tricky part, clone old hd0 to new drive. I used procedure described [here]("http://http://ubuntuforums.org/showthread.php?p=7534493#post7534493") using dd.

> dd if=/dev/sda of=/dev/sdc bs=32256

Powered down system, plugged new drive into first sata plug and booted. Success.

3) Now I had to move the partitions and resize. Could be scary. In vista used native disk management utility:
Right click 'Computer' -> Manage. Then select 'Disk Management'. Partition editor comes up.
In order to resize VISTA C: part(which is main reason I am doing this in the first place) had to remove old Ubuntu root partition which I just copied. Then resized C part. Then create new partition on disk for D part, call it K. Copied everything I wanted from D to K. But I need to make K D. Changed D to some other letter (S). But now I could not change K to D. Uh-oh. Re-booted VISTA. Brought Disk Man again. Now I could change K to D. Re-booted again to be safe and verified that programs installed in D worked.

4) For second disk used gparted to re-format old Vista D part to ext3. Because of partition layout copied old /home to new part. Edited /etc/fstab, rebooted to make sure home was intact.

5) Finally deleted old /home part so to reclaim space using gparted. Then resize new /home part include deleted partition. I used Ubuntu 7.4 CD for this because I wanted to use gparted but home cannot be mounted to do resize. Might be other way to do this.  For some reason CD kept spontaneously mounting home filesystem causing apparent failures in the procedure. Even though gparted logged errors procedure worked. Hopefully newer CD version works better.

Just though I would post this in case it helps someone else as this forum helped me, :lolflag:

Now have clean system

---

### Post by CMOS4081 on 2009-07-15
Hi there,
I found your post searching for an issue of my own that is similar but less complicate I hope.
 
I have a single sata HDD with a vista and ubuntu for a total of 3 partitions, vista,ubuntu,swap.
 
I was thinking of going for an HDD twice the side but do not want to go thru the hassle of reinstalling everything. going from an full 500GB to a single 1TB drive.
400B~vista 100~ubuntu/swap.  I plan to keep 100GB for ubuntu and the rest for vista 900~ which is were i dump everything as i can access it from linux with ease.
 
What to you recommend?
 
I was going to try an acronis and then resize the windows and then boot of usb of ubuntu to rebuild the grub.
 
both os are 64bit. if that helps.

---

