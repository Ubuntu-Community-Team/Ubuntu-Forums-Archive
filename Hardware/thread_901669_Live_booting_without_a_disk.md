---
title: "Live booting without a disk"
date: 2008-08-26
forum: Hardware
---

### Post by CTRLurself on 2008-08-26
[NOTE] This is a revamping of another thread found here: [http://ubuntuforums.org/showthread.php?t=898024](http://ubuntuforums.org/showthread.php?t=898024) This thread was started as an alternative to it, and it is linked as a reference, but this thread is attempting a slightly different goal.[/NOTE]

I'm attempting several things simultaneaously, and I need help with parts of everything.

1) I need a way to format a hard drive partition from command line into the iso9660 or CDFS format. The best I've found is *mkfs -t iso9660* or *mkfs -t cdfs* but neither of them work - however, *mkfs -t* does format the partition to ext2 if I just type *mkfs*, so I know I have access the the partition. 

**Question:** What format could I use with the mkfs command to format the partition like a CD/DVD (similar to cdfs or iso9660)? Or is there an alternate command to mkfs that would accomplish the same thing?

2) I need a way to "burn" the ISO file to the partition after it has been formatted correctly. Currently I'm doing the following:
> *sudo mount -o loop -t iso9660 /path/to/iso.iso /mnt/iso* mount the ISO file
*sudo mount /dev/sda /mnt/sda* mount the partition
*cp -R /mnt/iso/* /mnt/sda* copy-paste everything from one to the other
*umount /mnt/sda* unmount the partition

**Question:** Is there an easier way to get the ISO file onto the partition such as forcing a piece of software to burn the ISO directly to the partition?

3) (I read several "boot from USB how-to" guides but they're all full of large holes)

In the Ubuntu 8.04 64-bit edition, what do I need to do to make the partition boot from the GRUB menu (just to test the install for functionality). The partition is (hd,0,4), or first hard drive, 5th partition. I put the initrd.gz, the linuz file, and the I added this entry to the menu.lst for GRUB, but I got a "Kernel must be loaded before initrd" error.
> title           LIVE partition
root            (hd0,4)
kernal          /boot/vmlinuz-2.6.24-16-generic root=/
initrd          /boot/initrd.gz
I also tried this with just "vmlinuz" with just the root=/ after it and it didn't work either.
[B]
Question:[/B] What would my GRUB entry need to be to make this work from my GRUB menu on boot to test the installation process? And what files need to be in the /boot folder if any on the partition to make this boot like a live CD would?

4) I attempted all of this on a flash drive (instead of a partition) so I could go to somebody else's computer and boot my live CD with no disk. I've tried on many occasions to use Syslinux to make the flash drive bootable as a stand-alone drive (skipping GRUB) but I cannot seem to get it to work. Again, I've read A LOT of different how-to's for syslinux, but again they all seem to make the assumption you are using their specific ISO (usually SUSE, or ubuntu 6.06) or you already have extensive knowledge of using other boot managers. 

I've downloaded and installed syslinux, formatted the flash drive as fat32 (I tried also fat16, ext3, and ext2) marked the flash drive as bootable, and run syslinux to put the "isolinux" file onto the flash drive, I created the menu file, but I cannot figure out how to get it to actually function.

**Question:** Could you please post your most recent and descriptive guide for syslinux or another functional boot loader (my most recent was based on 7.06 which still didn't work)? 

**Question 2:** Anybody know of a boot loader that would automatically read an ISO so that I could skip having to do the first 2 parts of this post (and how to use it)? 

**Question 3:** A line-by-line post of the terminal commands for syslinux would be preferred, but I know it's the most difficult, so if somebody wouldn't mind helping me out that would be fantastic.

Thank you to everybody who actually took the time to read this, and any help that the community can offer would be greatly appreciated, and of course, once I get this functional I will post a DETAILED guide for how to get it all working so nobody else will have to go through this.

And sorry that I have so many questions, but this is my 4th day getting into the nitty-gritty of Ubuntu.

---

### Post by CTRLurself on 2008-08-26
Nobody?

---

