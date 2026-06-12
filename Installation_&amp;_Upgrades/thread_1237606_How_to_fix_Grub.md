---
title: "How to fix Grub?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by soxy on 2009-08-11
[SIZE=2]On my Windows laptop, I recently added Ubuntu and then Fedora (in that order). Fedora wrote over GRUB and installed it's own version. Now I can't boot Ubuntu. This is how my drive is partitioned:[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]sda1  NTFS[/SIZE]
 [SIZE=2]sda2  Linux swap[/SIZE]
 [SIZE=2]sda3 ext3 (Ubuntu)[/SIZE]
 [SIZE=2]sda4 (extended)[/SIZE]
 [SIZE=2]  -sda5  ext3 (Fedora)[/SIZE]
 [SIZE=2]  -sda6  ext3 (empty)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]The error message I'm getting is:[/SIZE]
                                  VFS: Cannot open root device sda3
 Please append a correct “root=” boot option


[SIZE=2]I have edited my GRUB file to include Ubuntu like this:[/SIZE]
                                  ```
[SIZE=2]#          all kernel and initrd paths are relative to /, eg.  [/SIZE] 
[SIZE=2]#          root (hd0,4)  [/SIZE]
 [SIZE=2]#          kernel /boot/vmlinuz-version ro root=/dev/sda5  [/SIZE]
 [SIZE=2]#          initrd /boot/initrd-version.img  [/SIZE]
 [SIZE=2]#boot=/dev/sda  [/SIZE]
 [SIZE=2]default=0  [/SIZE]
 [SIZE=2]timeout=5  [/SIZE]
 [SIZE=2]splashimage=(hd0,4)/boot/grub/splash.xpm.gz [/SIZE]
 [SIZE=2]hiddenmenu  [/SIZE]
 [SIZE=2]title Fedora (2.6.29.4-167.fc11.i686.PAE)  [/SIZE]
 [SIZE=2]        root (hd0,4)  [/SIZE]
 [SIZE=2]        kernel /boot/vmlinuz-2.6.29.4-167.fc11.i686.PAE ro root=UUID=17152038-c225-4eb0-8ca7-15$  [/SIZE]
 [SIZE=2]        initrd /boot/initrd-2.6.29.4-167.fc11.i686.PAE.img  [/SIZE]
 [SIZE=2]title Windows XP  [/SIZE]
 [SIZE=2]        rootnoverify (hd0,0)  [/SIZE]
 [SIZE=2]        chainloader +1  [/SIZE]
 [SIZE=2]title Ubuntu 6.06  [/SIZE]
 [SIZE=2]        root (hd0,2)  [/SIZE]
 [SIZE=2]        kernel /boot/vmlinuz-2.6.15-26-386 ro root=/dev/sda3[/SIZE]

```

[SIZE=2]Any suggestions?[/SIZE]

---

### Post by ZaHACKieL on 2009-08-11
Maybe this helps

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by schnelle on 2009-08-11
This helped me few months ago:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by soxy on 2009-08-11
Solved.

I had to change this:
```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3
``` to this:
```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/**hda3**
```I also needed a initrd statement. But I thought that was only needed if you had SCSI devices:-k
```
initrd /boot/initrd.img-2.6.15-26-386
```

---

### Post by ZaHACKieL on 2009-08-11
soxy, remember to mark the thread as solved

ZL

---

