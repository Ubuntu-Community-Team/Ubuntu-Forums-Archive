---
title: "Dell xps 1530: inst Linux with Vista and MD"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by LK_gandalf_ on 2008-02-14
hi all. I have an xps (fantastic :D) M1530 with a 250gb hard disk, here the partitions:

1) 118 MB, configuration EISA (?)
2) 2,5 GB, dell media direct (primary)
3) 220 GB, Windows Vista (primary)
4) 10 GB, Recovery (primary)

I'd like to install Ubuntu WITHOUT format pre-installed Vista and Media Direct. How can i do? Anyone has already done this?

Do you think it'll work if:
- delete the recovery and EISA partition (there are the CDs if any problem)
- resize the vista partition
- install ubuntu on the new space (and with a little swap partition) 
- install grub on the linux partition
?
Thank you very much in advance.

---

### Post by jan quark on 2008-02-14
well I have done this some times 

resize the vista partition in vista,

and install ubuntu on the blank partition

here is a guide how to set up a dual boot with vista ubuntu

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


PS: after a while I completely removed vista from my dell laptop :lolflag:

---

### Post by LK_gandalf_ on 2008-02-14
> **jan quark said:**
> well I have done this some times 

resize the vista partition in vista,

and install ubuntu on the blank partition

here is a guide how to set up a dual boot with vista ubuntu

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)


PS: after a while I completely removed vista from my dell laptop :lolflag:

But there arent' any problems with the media direct? I read that after a change in the partitions it could give problem..

---

### Post by jespdj on 2008-02-15
I would recommend to not delete the 118 MB "EISA" partition. It contains diagnostic tools that can be run without booting an operating system. These might be useful someday. Also, the partition is just 118 MB, which is tiny compared to the size of the whole disk, so you won't gain a lot of disk space by deleting it.

I have an XPS M1330 with 160 GB disk and left the EISA partition, deleted the MediaDirect / Vista / recovery partitions and then installed Vista on a small (20 GB) partition and used the rest of the disk for an Ubuntu ext3 partition and a small Ubuntu swap partition.

---

### Post by LK_gandalf_ on 2008-02-15
So you remove the media direct too...
I'd like to install ubuntu without touch Vista and media Direct...

---

### Post by spacesearcher on 2008-03-20
did you ever get it to work? Im getting the same system soon and want to do the exact same thing. I found this for the M1330 which from what I understand is very similar.
[http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
I don't know if it for sure works with M1530 but its the closest thing to what we want I think. but it does require you delete all of your partitions. but I have been told to just zero the disk instead. *shrug* I don't know which is best.

---

### Post by JOBUME on 2008-04-10
Hi, 

I installed Ubuntu 7.10 alongside Vista and Media Direct on my Dell XPS1530 yesterday. Here is how I did it:

1. Shrunk the Vista-partition with the vista partition manager (see: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm))

2. Booted Ubuntu from LiveCD
3. Choose Manual Partition (not guided)
4. Created one ext3 partition for Ubuntu and one partition for swap on the unused space freed by Vista partition manager. I created a swap as large as my RAM, altough I'm not exactly sure if this is needed
5. Finished the installation and now I have MediaDirect, Vista and Ubuntu working fine

I am a complete beginner at Linux and computers in general but thanks to forums and nice guides I managed to get it to work.

// Jonas, SWE

---

### Post by semiconductor on 2008-05-09
But how can you add another partitions when there are already 4?
Im a newby and have completely messed up all partitions and OS's. Nothing works. Windows after completely fresh reinstalling does not even work properly now.
Im screwed!!!
i give Ubuntu credit for getting all the drivers to work without any trouble which even a fresh dell install inst doing. B:ut it took 10 hours to move my partition after I deleted my 10 gig reinstal partition and then windows did not work anyway.
:(:(:(
Gparted just gives me endless error messages about not enough this or that. None of which is covered in dual OS install guides. I have not managed to get even a broken vista/ubuntu to instal yet. I have started from scratch many times and followed many guides like the one above.
novice DELL xps users beware!!!

---

