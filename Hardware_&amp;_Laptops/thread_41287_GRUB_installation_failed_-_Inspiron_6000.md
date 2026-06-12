---
title: "GRUB installation failed - Inspiron 6000"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Rishabb on 2005-06-12
Hi all,

I recently bought a dell inspiron 6000 and tried installing the ubuntu (hoary hedgehog) OS.

I have windows XP SP2 OS installed in it. During the middle of ubuntu installation, the grub failed saying that "Grub loader installation Failed" (it also mentioned it as Fatal Error). I couldnt proceed further and I exited the installation.

My windows xp works normally after I did a cold reboot. 

Can anyone please help in getting the grub installed in my laptop.

Thanks.

Regards
Rishabb

---

### Post by jerrykenny on 2005-06-17
Maybe write protection for mbr is ON,  check the bios setting for this.

---

### Post by sf-andrew on 2005-06-18
[QUOTE=jerrykenny]Maybe write protection for mbr is ON,  check the bios setting for this.[/QUOTE]
 I am having the same problem - how do I change the BIOS setting for this? When I went into the BIOS setup, there was nothing there that mentioned mbr.

---

### Post by awilisch on 2005-06-19
I have a Thinkpad A31 and I'm having the same problem. I HAD Ubuntu 5.04 installed before and I just recently reinstalled and repartitioned the laptop with a 10 gig primary XP partition, a 10 gig partition I created for Linux, a 500 meg swap partition and the rest as a data partition. The XP and data partitions are formatted with NTFS. I created all of the partitions in Windows, I just didn't format the 10 gig linux and swap partitions. I know grub will install cause as I said I've had it on here before, but this time it doesn't seem to want to install. 

oh, also the primary Xp partition is hda1, the other partitions are created inside an extended partition.  I tried installing grub to hda5, which is where linux is installed, but that failed as well. 

Any help is appreciated.

---

### Post by bullpa on 2005-06-19
I just installed Ubuntu on my new 6000, so I think it might help.
I Used partition magic to change the partition -  left some 16GB free space for linux.
During installation, I also met the same problem - "grub installation failed". The problem was because of partition magic as I discovered, or maybe it was ubuntu ;) I found the partition type was set 'vfat', so grub refused to install. I fixed the error, and everything was fine.

I would suggest:
Pressue Alt+F2 to open a terminal, and press ENTER to activate.
> umount /target  (You need to double check if this mount point is correct)
> fdisk /dev/sda
list the partitions to see if the linux partition type is '83', if not, change it back. 
then
> mount /dev/sda /target
either go back to GRUB installation procedure to try to install it again, or chroot /target, and grub-install /dev/sda.

Good luck!

---

### Post by mikejr on 2005-06-19
I had the same problem - I was installing in a partition that previously had Suse on it - and the grub install failed several times before it finally took.  

You could always install your own bootloader like Grub or Lilo using a boot CD.  As far as I could tell - the boot/grub/ info was present - so all you really would need to do is install the boot loader into the MBR.

---

