---
title: "boot problem ACER Aspire 5520-5716 laptop"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by Beowulf.1000 on 2008-02-01
**[COLOR="Red"]NOTE: Problem solved since I first posted this-- see my own thread for the solution[/COLOR]**. :guitar:
----
I could use some help! (this laptop has been a nightmare getting-- I have gone through hell and back dealing with Acer and the vendor to get it replaced when it initially had a red dot staring at me, a defective pixel, now I just need to get it working, first step is a working dual boot laptop as I really need WinXP for some apps that will not run on Ubuntu [Sony ACID Pro, Sony Vegas, Corel Painter X]):

I installed WinXP and Ubuntu 7.10 to my new Acer Aspire 5520-5716 laptop but now when I choose WinXP from the Grub menu, WinXP starts to load, then I get a blue scree of death with error codes. Ubuntu boots fine from grub.

[LIST=1]
[*]I first took out the factory drive that had Windows Vista and Acer stuff before even booting the laptop, replaced that with a spanking new Hitachi 200GB drive. 
[*]Then used GParted to partition the drive into /dev/sda1 NTFS and /dev/sda2 ext3 and /dev/sda3 swap partitions. 
[*]Then installed WinXP to the ntfs partition (WinXP booted fine at this point)
[*]Then installed Ubuntu to the ext3 partition
[*]Now Ubuntu boots fine but WinXP goes to a blue screen with error codes after first showing the logo and appearing to start to.
[/LIST]

When WinXP crashes to the blue screen, it reports this on the blue screen:
  UNMOUNTABLE_BOOT_VOLUME
 *STOP: 0X000000ED (0X893BFC08, 0XC000014F, 0X00000000, 0X00000000)

---

### Post by Beowulf.1000 on 2008-02-01
I reinstalled WinXP, am now reinstalling Ubuntu and going to see if there is some way to install grub to hda2 (hd0,1), I don't know, I am open to ideas. Frustrating. A clean drive, one would think it would go smooth, maybe it is some issue with Acer's BIOS not wanting me to do this?

> **Beowulf.1000 said:**
> I could use some help! ...
When WinXP crashes to the blue screen, it reports this on the blue screen:
  UNMOUNTABLE_BOOT_VOLUME
 *STOP: 0X000000ED (0X893BFC08, 0XC000014F, 0X00000000, 0X00000000)

---

### Post by Beowulf.1000 on 2008-02-01
Problems solved! :guitar:  I have WinXP and Ubuntu 7.10 installed on the Hitachi 200GB drive, dual boot. My brain is fried, so here is the short solution: Use gparted (version 0.3.4-11 is what I used) to partition the 200GB laptop drive (I yanked the factory installed 160GB drive, did not even boot it) into partitions less than 80GB (I made a 75GB ntfs, 50GB ext3, and a 1GB swap, the remainder unallocated). I reasoned the Acer Aspire BIOS could not handle partitions over 80GB because the factory installed default hard drive comes as an 80GB ntfs with MS Vista and an 80GB partition for Data. Then I installed WinXP to the ntfs. Then I installed Ubuntu and when it got to the partitioner step I click the option for "Guided Partitioning - Use Largest Free Space".  It worked. Rebooted and Grub appears, and I can boot to WinXP or Ubuntu.

Prior to the above, I had partitioned about 130GB or even a 100GB ntfs and the rest for ext and swap, but when I went to install WinXP, the WinXP setup kept just seeing the large 'unrecognized'  partition', would 'install' but not really, because a reboot would show it corrupted, and an Ubuntu install would show the entire drive as wiped out with no formatted partitions, very odd. Like I said, I figure the BIOS just got confused with partitions over 80GB, so I kept them down to about 75GB or less and it all then went fine.
 :):):):)

---

### Post by mc00 on 2008-02-19
> **Beowulf.1000 said:**
> Problems solved! :guitar:  I have WinXP and Ubuntu 7.10 installed on the Hitachi 200GB drive, dual boot. My brain is fried, so here is the short solution: Use gparted (version 0.3.4-11 is what I used) to partition the 200GB laptop drive (I yanked the factory installed 160GB drive, did not even boot it) into partitions less than 80GB (I made a 75GB ntfs, 50GB ext3, and a 1GB swap, the remainder unallocated). I reasoned the Acer Aspire BIOS could not handle partitions over 80GB because the factory installed default hard drive comes as an 80GB ntfs with MS Vista and an 80GB partition for Data. Then I installed WinXP to the ntfs. Then I installed Ubuntu and when it got to the partitioner step I click the option for "Guided Partitioning - Use Largest Free Space".  It worked. Rebooted and Grub appears, and I can boot to WinXP or Ubuntu.

Prior to the above, I had partitioned about 130GB or even a 100GB ntfs and the rest for ext and swap, but when I went to install WinXP, the WinXP setup kept just seeing the large 'unrecognized'  partition', would 'install' but not really, because a reboot would show it corrupted, and an Ubuntu install would show the entire drive as wiped out with no formatted partitions, very odd. Like I said, I figure the BIOS just got confused with partitions over 80GB, so I kept them down to about 75GB or less and it all then went fine.
 :):):):)

It's funny I have 5520 formatted the 160(SATA) and put xp on it work fine... now the question is would have to do this if I try to install ubuntu to avoid any hang or kernel panics?

---

### Post by jsimmons on 2008-03-16
I just got a 5520-5716 with the 160gb drive and it has two partitions on it (actually, it has three if you count the rescue partition).  I am curious to know what BIOS version you guys are running.  I have 1.08 on my machine, but from the acer europe support site has v1.30 available.

Maybe the bios revision is the key.

---

