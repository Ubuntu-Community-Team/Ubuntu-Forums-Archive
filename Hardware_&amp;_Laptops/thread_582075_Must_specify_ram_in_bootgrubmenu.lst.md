---
title: "Must specify ram in /boot/grub/menu.lst"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by hamster_billy on 2007-10-19
I recently added more memory to my laptop, upgrading from 1 Gb (2 x 512 Mb) to 2 Gb (2 x 1 Gb). I read about problems other people had had doing this before I started - the major problem being that if both sticks were replaced Ubuntu would hang on boot, but if they were replaced one at a time, booting first at 1.5 Gb then at 2 Gb, everything would be fine and dandy.

What I found was, indeed, that Ubuntu would hang with 2 Gb, swapping both sticks at first, and would be happy when I swapped one back to give it 1.5 Gb. But it would still hang when I swapped in the second 1 Gb stick, contrary to what most other people reported.

In the end I found I had to specify the amount of memory in /boot/grub/menu.lst, thus the relevant lines read:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea2fc7bf-8894-4710-bd0a-d69d2d816e1e ro quiet splash nmi_watchdog=0 mem=2011M
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
The 'nmi_watchdog=0' is there to make Virtualbox work.

Because of this, every time I upgrade the kernel (as I did today), which rewrites the grub menu, I have to boot into safe mode and add 'mem=2011M' before I can boot normally. It's pretty annoying. Thus I have two questions:
1 - Is there a way to specify that I want that option included when the file is automatically generated?
2 - Why must I specify the amount of memory in the first place? Is this a motherboard issue rather than an Ubuntu issue?

---

### Post by dhon_ on 2007-10-19
You need to change the kernel options in the
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bddeee95-b54c-443c-8e44-7dd06245f320 ro
```
section of /boot/grub/menu.lst and then run
```
sudo update-grub
```

Not sure about why you'd need it though.

---

### Post by hamster_billy on 2007-10-19
Cool. Thank you. I'll play with it in the morning - don't want to screw it up now by being tired. ;-)

---

### Post by hamster_billy on 2007-10-21
All is good. Thanks very much. Recovery mode was always very slow, but now, with memory specified in its grub entry too, is far faster.

---

### Post by L8erG8er on 2007-10-21
hamster_billy, can you post your changed section of menu.lst so I can see what you did?

Thanks!

---

### Post by hamster_billy on 2007-10-26
This is the section I edited, so that I got what I needed after a grub-update - adding the options to the last line shown did the job.
```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ea2fc7bf-8894-4710-bd0a-d69d2d816e1e ro nmi_watchdog=0 mem=2011M

```

And this is the boot menu entry for my Gutsy.
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ea2fc7bf-8894-4710-bd0a-d69d2d816e1e ro nmi_watchdog=0 mem=2011M quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

---

### Post by hamster_billy on 2007-10-26
I just worked out how to switch on email notification of replies, so it shouldn't take me 5 days to reply in future. ;-)

---

