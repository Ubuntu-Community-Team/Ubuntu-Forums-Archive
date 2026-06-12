---
title: "GRUB &amp; Recovery Partitions"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by notwen on 2007-09-11
Hello, I have one of the new Dellbuntu Inspiron 1420n laptops.  I'm dual-booting the pre-installed Feisty Fawn and a -working- WindowsXP install.  That said, in the process of installing Windows XP the MBR was installed onto one of Dell's pre-made recovery partitions.  This causes issues when booting into Windows XP I go through GRUB & the windows boot-loader, although when I reboot from Windows XP I am greeted with the Windows boot-loader, not GRUB(I was stuck using the gParted LiveCD to constantly remove the boot flag from the partition w/ MBR and re-add the boot flag to the GRUB partition).  I have some-what fixed this by hiding this recovery partition using the gParted LiveCD.  I was wanting to know if it is possible to somehow have GRUB launch Windows directly instead of bringing me to the Windows boot-loader?  

Hope that all makes sense.  Please post if you need/desire more info.  Thanks. =]

---EDIT---
I have attached a screenshot of my partition table in gParted.  **sda1** and **sda**2 are both part of Dell's recovery and I would like to leave this intact.  MBR was installed to **sda2** during my Windows XP installation instead of **sda7** where Windows was installed.  GRUB is located in **sda3**, the /boot partition.  I currently have **sda3** with the boot flag and **sda2** with the hidden flag.  Hope this helps clear things up.

---

### Post by eggdeng on 2007-09-11
If what you want to do is point grub  directly to sda7, the XP partition, you could try changing the current XP section in /boot/grub/menu.lst to
```
title		Windows XP
root		(hd0,6)
chainloader	+1
```
In any case, it would be an idea to post your /boot/grub/menu.lst.

---

### Post by notwen on 2007-09-11
> **eggdeng said:**
> If what you want to do is point grub  directly to sda7, the XP partition, you could try changing the current XP section in /boot/grub/menu.lst to
```
title		Windows XP
root		(hd0,6)
chainloader	+1
```
In any case, it would be an idea to post your /boot/grub/menu.lst.

I'll give this a try once I'm home and if it doesn't work I'll post my menu.lst once I'm home.  Thanks for the suggestion. =]

---

### Post by notwen on 2007-09-11
> 
title		Windows XP
root		(hd0,6)
chainloader	+1


Changing from (hd0,1) to (hd0,6) returns this when I select Windows XP from GRUB menu, hd0,1 will atleast bring me to the windows boot-loader.

> 
Error 12: Invalid device requested
Press any ket to continue


Here is my menu.lst reflecting the change eggdeng recommended.  Any other recommendations?
 
```


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=44327780-068d-4378-a236-374d6c548b9b ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=44327780-068d-4378-a236-374d6c548b9b ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

title		Windows XP
rootnoverify		(hd0,6)
makeactive
chainloader	+1
### END DEBIAN AUTOMAGIC KERNELS LIST

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz

```

---

### Post by notwen on 2007-09-12
*bump*

---

