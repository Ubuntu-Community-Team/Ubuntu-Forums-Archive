---
title: "finally solved hibernate issue dell vostro 1400"
date: 2008-07-05
forum: Hardware
---

### Post by empty_tank on 2008-07-05
i have finally solved the last remaining issue in installing hardy on my dell vostro 1400 which is hibernate.

My specs are: 
	Intel Core 2 Duo (1.66.Ghz), 
	4 GB DDR2 SDRAM, 
	120 GB HDD, 
	integrated Intel Graphics and wireless, 
	Sigmatel 9928 Audio,
	Conexant HDA D330 MDC Modem 

I never had problems with suspend, only with hibernate. During hibernation, the laptop harddrive led lights up before shutting down.  After pressing the power button, the computer reboots.  Pretty frustrating.

After looking around for an answer, I came across an ArchLinux tutorial at [http://archux.com/page/setting-laptops](http://archux.com/page/setting-laptops) which solved the problem.

It suggests editing the "/boot/grub/menu.lst as root with your favourite text editor".  In ubuntu this is what I did:

1. gksu gedit /boot/grub/menu.lst
2. go down to the 

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35356d12-8bee-4808-b68a-72884a49b8a6 ro splash rootflags=data=writeback 
initrd		/boot/initrd.img-2.6.24-19-generic


and add "resume=/dev/[your swap partition]" to the kernel line


Since my swap partition is sda5, then my menu.lst reads:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=35356d12-8bee-4808-b68a-72884a49b8a6 ro splash rootflags=data=writeback resume=/dev/sda5
initrd		/boot/initrd.img-2.6.24-19-generic


I hopes this fix works for you.

If you don't know your swap partition, look at /etc/fstab

---

### Post by 4ugeistr on 2009-03-18
Thanks! It helped and hibernate worked fine on my dell vostro 1400 in 8.10
But had to copy the *rootflags=data=writeback* piece also since it was absent.

---

### Post by inspired on 2009-03-19
Great. Thanks. This has at long last solved my hiberation issues.

Jonathan

---

