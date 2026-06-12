---
title: "Problem with boot menu!"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by zking on 2009-09-22
When I boot up my computer, the menu gives me the options to boot into one of these operating systems: 
[B]
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        2fb78eda-4f0e-446d-baae-fdf440a32f66
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fb78eda-4f0e-446d-baae-fdf440a32f66 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        2fb78eda-4f0e-446d-baae-fdf440a32f66
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=2fb78eda-4f0e-446d-baae-fdf440a32f66 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2fb78eda-4f0e-446d-baae-fdf440a32f66
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fb78eda-4f0e-446d-baae-fdf440a32f66 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2fb78eda-4f0e-446d-baae-fdf440a32f66
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2fb78eda-4f0e-446d-baae-fdf440a32f66 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2fb78eda-4f0e-446d-baae-fdf440a32f66
kernel        /boot/memtest86+.bin
quiet[/B]
[B]
title Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1[/B]



For some reason, "**Ubuntu 9.04, kernel 2.6.28-11-generic" **and **"Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)" **show up twice in the boot menu. Did I accidentally install Ubuntu twice? How do I fix this?

---

### Post by snowpine on 2009-09-22
Hi Zking, when you updated your computer, you got a new kernel (2.6.28-15). Ubuntu keeps the old kernel (2.6.28-11) so you can boot into it in case there's a problem. Each kernel has a recovery mode as well, in case you need it. Your menu looks normal to me.

ps You can tell you have one Ubuntu install and not two by comparing the UUID numbers... they are identical, therefore all of your Ubuntu is installed on the same partition.

---

### Post by zking on 2009-09-22
> **snowpine said:**
> Hi Zking, when you updated your computer, you got a new kernel (2.6.28-15). Ubuntu keeps the old kernel (2.6.28-11) so you can boot into it in case there's a problem. Each kernel has a recovery mode as well, in case you need it. Your menu looks normal to me.

ps You can tell you have one Ubuntu install and not two by comparing the UUID numbers... they are identical, therefore all of your Ubuntu is installed on the same partition.

Oh, okay. Thanks for the help. :)

---

### Post by mbaggia on 2009-09-22
> **snowpine said:**
> when you updated your computer, you got a new kernel (2.6.28-15). Ubuntu keeps the old kernel (2.6.28-11) so you can boot into it in case there's a problem. Each kernel has a recovery mode as well, in case you need it. 

I have three kernels in my GRUB menu. Is there any way of getting rid of old ones to free up disk space?

Thanks,
Masood

---

### Post by snowpine on 2009-09-22
> **mbaggia said:**
> I have three kernels in my GRUB menu. Is there any way of getting rid of old ones to free up disk space?

Thanks,
Masood

Yes; you can remove old kernels in the Synaptic package manager. Look for the linux-headers and linux-images packages, and be sure to remove the correct versions.

I recommend keeping at least two kernels so you always have a spare.

---

### Post by drs305 on 2009-09-22
mbaggia,

You can remove them via synaptic, as mentioned in the previous post, or hide them in the menu.lst. You can do this manually or using a grub tweaking app called StartUp-Manager. It's a great GUI menu editor for Grub.

This guide discusses SUM but also contains a section on how to remove the kernel displays (including how to remove them with Synaptic):
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by snowpine on 2009-09-22
Hiding them in the grub list will not accomplish Masood's stated goal of freeing up disk space.

---

### Post by drs305 on 2009-09-22
> **snowpine said:**
> Hiding them in the grub list will not accomplish Masood's stated goal of freeing up disk space.

That's why I referenced the section of the guide which discusses specifically which files to remove via Synaptic. But you are correct and I could have been clearer.

---

### Post by mbaggia on 2009-09-22
Thank you both for the advice! :P

---

### Post by Lieter on 2009-09-22
You can use apt-get to remove the old kernels:

```
sudo apt-get remove linux-image-2.6.28-XX-generic
```

Where XX is the kernel you want to remove. Doing this will also remove the entries froom the boot menu

---

