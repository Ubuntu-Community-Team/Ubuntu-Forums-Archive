---
title: "inspiron 6000 dual boot"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by rmdnet on 2005-07-13
Hi, I have installed Ubuntu on my Dell Inpiron 6000 and now I can not boot WinXP

my menu.lst is the following:

[COLOR=Red]

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		DELL Disgnostics 
root		(hd0,0)
makeactive
chainloader	+1

title		Win XP 
rootnoverify	(hd0,1)
makeactive
chainloader	+1[/COLOR]


Am I doing something wrong?

Thanks a lot

---

### Post by nemin on 2005-07-13
[QUOTE=rmdnet]Hi, I have installed Ubuntu on my Dell Inpiron 6000 and now I can not boot WinXP[/QUOTE]
Your menu.lst looks good. Can you tell exactly what happens when you try to boot Windows XP? An error message or something?

---

