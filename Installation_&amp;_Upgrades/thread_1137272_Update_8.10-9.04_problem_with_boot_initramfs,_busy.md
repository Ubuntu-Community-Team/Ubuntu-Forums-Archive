---
title: "Update 8.10-9.04 problem with boot: initramfs, busybox"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by kkrzysiek on 2009-04-25
Hello!
I'm Ubuntu beginner and I have a problem. After updating 8.10 to 9.04 and restarting computer, my linux doesn't start in normal mode but in text mode:"

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
     -Check rootdelay= (did the system wait long enough?)
     -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/310147a9-f21c-4e7c-aeb0-18f31073da58 does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

kernel 2.6.27-11-generic

I don't know how to repair it & I don't want to come back to Windows but if I won't repair it, it may happen.

Please, help me!

Hardware:
AMD Athlon 64 x2 dual core QL60 1.9
ATI Radeon HD3200
4GB DDR2 RAM
250GB HDD

---

### Post by jmomandia on 2009-04-27
Same problem here.

---

### Post by pnjunkie on 2009-04-27
> **kkrzysiek said:**
> 
ALERT! /dev/disk/by-uuid/310147a9-f21c-4e7c-aeb0-18f31073da58 does not exist. Dropping to a shell!


I think the issue right there is your menu.lst file. 

Yours probably looks like this

[I]title        Ubuntu 9.04
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic **root=/dev/disk/by-uuid/310147a9-f21c-4e7c-aeb0-18f31073da58** does not exist ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
boot[/I]

And it should look more like this:

[I]title        Ubuntu 9.04
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic** root=/dev/sda1** ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
savedefault
boot[/I]

You'll need to boot with a live cd to take a look at it.

---

### Post by kissme_caitlin on 2009-04-28
regarding the startup issue "Gave up waiting for root device" that leaves the user at initramfs prompt

 I was able to fix this problem by editing /boot/grub/menu.lst    (edit the file by opening a terminal and typing sudo gedit /boot/grub/menu.lst)  Scroll down to the bottom of the file.

Initially my menu.lst looked like this:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        254139e0-a67c-4d72-b7c1-442b616f6dc9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=254139e0-a67c-4d72-b7c1-442b616f6dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```


I added rootdelay=90 before the word splash, so it looks like this:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        254139e0-a67c-4d72-b7c1-442b616f6dc9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=254139e0-a67c-4d72-b7c1-442b616f6dc9 ro quiet rootdelay=90 splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

This [link]("http://ubuntuforums.org/showthread.php?p=7165168") may be helpful.

---

### Post by qneill on 2009-12-14
Most likely related to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360378)
-- 
Quentin

---

