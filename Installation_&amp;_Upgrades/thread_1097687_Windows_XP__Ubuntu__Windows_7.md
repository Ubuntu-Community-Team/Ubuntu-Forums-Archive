---
title: "Windows XP / Ubuntu / Windows 7"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by JG53_Jaguar on 2009-03-16
Hi All,

I have 2 partitions on my hard drive on my laptop, the primary partition is for Windows XP and the other is for Ubuntu. I got the beta version of Windows 7 (Build 7022), so I dropped the Ubuntu partition and on that partition I installed Windows 7. So I can now dual boot to Windows XP and Windows 7...at some point in the near future I would like to drop the Windows 7 partition and install there Ubuntu again...can I do this without loosing the Windows XP partition?

Thanks for your help!

---

### Post by mhgsys on 2009-03-16
Well you could remove the windows 7 partition with a live cd, using gparted.
Or you could use the partitioner which will load during install.

And install ubuntu again on that partition

---

### Post by JG53_Jaguar on 2009-03-16
> **mhgsys said:**
> Well you could remove the windows 7 partition with a live cd, using gparted.
Or you could use the partitioner which will load during install.

And install Ubuntu again on that partition

That's cool, thanks for your help! I just though that perhaps 8.10  would not be able to figure out the boot sector since 8.10 would know how to handle Windows 7 but I guess Windows 7 is essentially windows Vista...

thanks again!

---

### Post by theozzlives on 2009-03-16
> **JG53_Jaguar said:**
> That's cool, thanks for your help! I just though that perhaps 8.10  would not be able to figure out the boot sector since 8.10 would know how to handle Windows 7 but I guess Windows 7 is essentially windows Vista...

thanks again!

It should've been Vista SP2

---

### Post by mhgsys on 2009-03-16
> **JG53_Jaguar said:**
> That's cool, thanks for your help! I just though that perhaps 8.10  would not be able to figure out the boot sector since 8.10 would know how to handle Windows 7 but I guess Windows 7 is essentially windows Vista...

thanks again!

ehmz, 
It doesn't seem to matter if 8.10 would know how to handle vista bootloader
Important thing is that it can recognize the partition, because that's what you want to remove right?

---

### Post by JG53_Jaguar on 2009-03-16
> **mhgsys said:**
> ehmz, 
It doesn't seem to matter if 8.10 would know how to handle vista bootloader
Important thing is that it can recognize the partition, because that's what you want to remove right?

Yes correct, essentially I just want to make sure that Ubuntu 8.10 will recognize XP being on primary partition ( I will drop the Windows 7 partition from XP disk manager before I install Ubuntu 8.10) and then modify the boot parition and install to boot loader I'm hoping that Windows 7 won't leave some stuff behind that will confuse Ubuntu 8.10

---

### Post by mhgsys on 2009-03-16
> **JG53_Jaguar said:**
> Yes correct, essentially I just want to make sure that Ubuntu 8.10 will recognize XP being on primary partition ( I will drop the Windows 7 partition from XP disk manager before I install Ubuntu 8.10) and then modify the boot parition and install to boot loader I'm hoping that Windows 7 won't leave some stuff behind that will confuse Ubuntu 8.10

Well. 
If your gonna format the partition windows 7 won't be able to leave anything behind.
8.10 will detect XP.

---

### Post by Mark Phelps on 2009-03-16
> **JG53_Jaguar said:**
> Yes correct, essentially I just want to make sure that Ubuntu 8.10 will recognize XP being on primary partition ( I will drop the Windows 7 partition from XP disk manager before I install Ubuntu 8.10) and then modify the boot parition and install to boot loader I'm hoping that Windows 7 won't leave some stuff behind that will confuse Ubuntu 8.10

Since you installed Seven after XP, it most probably wrote its boot loader files to the XP partition -- which will remain there after you remove Seven.

But, given that you're going to install GRUB either to the MBR, or to the Ubuntu partition, that won't present a problem to Ubuntu.  It may, however, present a problem when you try later to boot back into XP.

---

### Post by JG53_Jaguar on 2009-03-17
> **Mark Phelps said:**
> Since you installed Seven after XP, it most probably wrote its boot loader files to the XP partition -- which will remain there after you remove Seven.

But, given that you're going to install GRUB either to the MBR, or to the Ubuntu partition, that won't present a problem to Ubuntu.  It may, however, present a problem when you try later to boot back into XP.

Thanks a lot Mark, I appreciate your input!

---

