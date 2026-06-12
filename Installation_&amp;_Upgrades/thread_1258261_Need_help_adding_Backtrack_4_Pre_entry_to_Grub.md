---
title: "Need help adding Backtrack 4 Pre entry to Grub"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by derrick1985 on 2009-09-04
Hi,

I installed Backtrack 4 pre (but not the boot loader) and then installed Ubuntu. My menu.lst file has all my Ubuntu listings working fine, but I don't have a working entry to Backtrack. I tried adding it manually, but it still won't work, says something doesn't exist. Can someone look over and tell me what I am missing?

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6fd3d37f-eaba-4e3e-857e-e75a9f85a30b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6fd3d37f-eaba-4e3e-857e-e75a9f85a30b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/memtest86+.bin
quiet

title		Backtrack 4 Pre
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.29.4 
initrd		/boot/initrd.img-2.6.29.4
quiet
```

According to my Ubuntu install, backtrack is on /dev/sda8 (so that would be hd0,8 right?) which I believe I tried to boot with when the above entry failed. (I edited uuid to root (hd0,8) ) and still it won't work. What am I missing from the entry? 

Thanks in advance,

---

### Post by IsmailBhai on 2009-09-25
> **derrick1985 said:**
> Hi,

I installed Backtrack 4 pre (but not the boot loader) and then installed Ubuntu. My menu.lst file has all my Ubuntu listings working fine, but I don't have a working entry to Backtrack. I tried adding it manually, but it still won't work, says something doesn't exist. Can someone look over and tell me what I am missing?

```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6fd3d37f-eaba-4e3e-857e-e75a9f85a30b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6fd3d37f-eaba-4e3e-857e-e75a9f85a30b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/memtest86+.bin
quiet

title		Backtrack 4 Pre
uuid		6fd3d37f-eaba-4e3e-857e-e75a9f85a30b
kernel		/boot/vmlinuz-2.6.29.4 
initrd		/boot/initrd.img-2.6.29.4
quiet
```

According to my Ubuntu install, backtrack is on /dev/sda8 (so that would be hd0,8 right?) which I believe I tried to boot with when the above entry failed. (I edited uuid to root (hd0,8) ) and still it won't work. What am I missing from the entry? 

Thanks in advance,

sda8 is hd0,7

if you cant boot try removing the initrd

---

### Post by rreese6 on 2009-09-25
I would remove the UUID (and number) then type in on the kernel line
root=/dev/sda8 at the end
like so:

kernel		/boot/vmlinuz-2.6.29.4 root=/dev/sda8

---

