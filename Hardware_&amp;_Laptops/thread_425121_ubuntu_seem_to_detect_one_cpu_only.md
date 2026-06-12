---
title: "ubuntu seem to detect one cpu only"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by zanjabeel5 on 2007-04-27
Hi 
I run feisty on lenovo c200, if I run ```
 cat /proc/cpuinfo 
```
I get this
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3329.09
clflush size    : 64

```

as you can see only one cpu is detected, but i'm sure my system is dual core ( it has a sticker on it)

what should i do ?

---

### Post by newlinux on 2007-04-27
If you do 

```
uname -a
```

and see SMP in the output you have a kernel that is using both cores. If you open up gnome-system-monitor and look at the Resources tab you should see two CPUs

If you don't see SMP you are probably running the wrong kernel...

---

### Post by zanjabeel5 on 2007-04-27
Thanks for your reply.

uname -a  shows non smp kernel
what should I do ?

---

### Post by newlinux on 2007-04-27
You will need to install and SMP kernel (the generic kernel is probably what you want)
can you post the output of uname -a

---

### Post by jpatton on 2007-04-27
My understanding is Ubuntu should detect and load the appropriate kernel I used the same Fiesty CD on my laptop, single core cpu, and on my other laptop, dual core cpu, and it showed both.

---

### Post by newlinux on 2007-04-27
Yes, the generic kernel should detect and use multiple cores if you have them, or work fine on single core systems as well. That's why we should confirm what kernel he/she is running first.

Did you check your gnome-system-monitor (I think that's what it is, I haven't used it in a while I just use htop) to see if it sees two cores?

---

### Post by zanjabeel5 on 2007-04-27
Here is the output of uname -a

Linux sab-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

---

### Post by newlinux on 2007-04-27
Alright. You are not running the right kernel. But it is probably installed. do you get a list of kernels to boot into when you boot up?

If you don't get a choice, try installing the generic kernel:

sudo apt-get install linux-image-generic

If it doesn't install anything (meaning it was already installed) then it is just a matter of you selecting the right kernel at boot.

Can you post the contents /boot/grub/menu.lst?

---

### Post by zanjabeel5 on 2007-04-27
[HTML]title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro single
initrd          /boot/initrd.img-2.6.17-11-386

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro single
initrd          /boot/initrd.img-2.6.15-26-386

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
[/HTML]

The first option is the default
( I upgradded all the way from ubuntu 6.06 )

---

### Post by newlinux on 2007-04-27
Did you try installing the linux-image-generic kernel?

None of the kernels listed in your menu.lst are SMP kernels. Did you see both processors before at any time?

---

### Post by zanjabeel5 on 2007-04-27
I installed linux-image-generic and it added this
[HTML]title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=735a3a59-ba12-4321-9694-af5711677404 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
[/HTML]

to my boot menu
when I boot to this option (was not set as default) then uname -a give me a result with SMP,
but unfortunately my wireless didn't work, so I rebooted to the default option to post this.

So thanks very much, i hope i can take from here (maybe install gnome-network-manager will help).

it's strange the the installer  ( the upgrade manager  in my case ) didn't do this automatically.

Thanks again. :)

---

### Post by newlinux on 2007-04-27
You're welcome, and it is strange that kernel wasn't installed. If you ever want to boot into the generic kernel by default you can modify menu.lst (put the generic kernel at the top). Just an FYI. Good luck with the wireless...

---

### Post by fwojciec on 2007-04-27
Try installing linux-restricted-modules-generic (not sure if this is the right apt-get package name, I usually do it via Synaptic) - it might help to get your wireless to work.

---

### Post by zanjabeel5 on 2007-04-28
> **fwojciec said:**
> Try installing linux-restricted-modules-generic (not sure if this is the right apt-get package name, I usually do it via Synaptic) - it might help to get your wireless to work.

That's what was needed. Actually ubuntu suggested installing this package when I tried to enable restricted drivers.

Thanks

---

