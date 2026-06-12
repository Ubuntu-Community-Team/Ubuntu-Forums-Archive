---
title: "Help! Cannot boot Ubuntu Partition, Very Detailed"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by justdont on 2009-03-27
Ok, I have Dual-booting machine XP and Kubuntu 7.10.  I have not booted into Kubuntu for a few months.  I tried to boot into Kubuntu by selecting it from the Grub Menu and I get something like this error

Error 17: Cannot Mount Selected Partition

This was at root(hd0,2). I figured this wasnt right... So, after reading the forums for a few hours I tried a few other things.  I went to the GRUB command prompt and did the following:

> find /boot/grub/stage1

I then used the returned info, and ran:

> root (hd0,3)
> setup (hd0)

It appeared to work. I returned return to the GRUB menu and  selected the Kubuntu Partition (which is now at root(hd0,3) instead of root(hd0,2) )and one of two things would happen 

1) Mostly it would say "Error 15: File not Found" or 
2) Once or twice, it would appear as if it were booting, then restart


I used a 7.10 LiveCD and ran the install to try and see where the drives where mounted.  I noticed that my Linux partition was not mounted to "/". I tried to change it, but a message said I would need to reformat. So i think there is an issue there. I canceled the installation and exited.

 Also while using the LiveCD, I tried to navigate to my ext3 filesystem, to back-up my data. The drive showed up just fine. But when I tried to explore it I got an error "hal-storage-fixed-mount refused uid 999"

I think there is some type of mounting issue. I am relatively new to Linux world and all help/comments/suggestions would be most helpful. Thanks. 


> sudo fdisk -l  returns:

/dev/sda1 * 1      7833  62818541    7  HPFS/NTFS
/dev/sda2   7834   25298 140287612+  f  W95 Ext'd (LBA)
/dev/sda3   25299  25422 996030      82 Linux swap / Solaris
/dev/sda4   25423  30401 39993817+   83 Linux
/dev/sda5/  7834   16566 70147791    7  HPFS/NTFS

---

### Post by pbpersson on 2009-03-28
You posted this 2 hours ago and no one has replied so I will take a stab at this.

Version 7.10 is Gutsy Gibbon.  It is very sad, but I don't know the numbers, I only know the cute animal names.  I should post a cross reference guide on the wall here. 

This is my recommendation:

Download and burn an Intrepid Ibex Live CD, boot from that, mount your NTFS and EXT3 partitions and backup your Linux data to NTFS and then install the new version.

I only say this because I don't know what old bugs you might have on that 7.10 CD and if anyone tries to help you they would need to dig out an old 7.10 CD to see how it works and most people don't want to travel back in time.

Having said that, it sounds like the steps you did with Grub should have worked.  I don't know why you are getting that error when you try to mount, but my instincts are telling me that you are dealing with bugs that might have been fixed in later versions.

---

