---
title: "Kernel Updated but not running"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by pizza-is-good on 2009-08-04
Hello all

Here is my problem:
My kernel has updated several times, I have seen the update on the update manager, the last one that I downloaded was 2.6.28-14, but when I go to the system monitor to see which on is running, it is still running 2.6.28.11 - generic, which if I'm not wrong, is the default one that was installed when I upgraded to jaunty.

My guess is that there is a setting somewhere that will automatically update it, and that I do not have enabled. There probably is a very simple solution, but I don't know what to do.

Thanks for your help in advanced

---

### Post by snowpine on 2009-08-04
You need to reboot and choose the new kernel from the Grub menu.

If it does not automatically get added to Grub (it should), try:

```
sudo update-grub
```

---

### Post by pizza-is-good on 2009-08-04
Sorry, that didn't work, but here is what came out in the terminal when I did, hopefully it helps
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done

```

---

### Post by snowpine on 2009-08-04
Do you have any other operating systems installed on the computer?

Also, please post the output of 

```
cat /boot/grub/menu.lst
```

---

### Post by pizza-is-good on 2009-08-04
Yes, I dual boot Ubuntu and Vista.

Here is the output of that:
```

#color black/black black/black
default         7
timeout 30

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
# kopt=root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive

```

Thanks for all your help

---

### Post by snowpine on 2009-08-04
Strange... well anyway, you should be able to do it by hand no problem.

```
gksu gedit /boot/grub/menu.lst
```

Copy one of the sections that says:

```
title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
```

Paste it, and then edit so it reads:

```
title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic
```

Hope that works, maybe someone else has an idea why it isn't updated automatically... :)

---

### Post by pizza-is-good on 2009-08-04
If you read what I have here before, never mind.

OK, solved it! I have already spotted some problems because of the new kernel, but they seem trivial.

Thanks for your help. Greatly appreciate it.

---

### Post by snowpine on 2009-08-04
Sorry, I mean within the document itself, using Gedit's copy and paste commands (Edit menu, or Ctrl+C, Ctrl+V). You want it to look like this (I left out the stuff at the beginning and end to make it easier to read:

```
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro  single
initrd /boot/initrd.img-2.6.27-11-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=f627c7cb-18bd-4ed9-b677-d9e972d5bfe6 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


```

In other words, you are creating a new entry that is identical to the old one except that the 11's are changed to 14's. Cool? :)

(you can add another one for 13 if you want that option too)

---

### Post by pizza-is-good on 2009-08-04
Look at my previous post. Sorry for having you write all that, I should have looked at it 30 more seconds before replying to you and I would have figured it out.

---

### Post by snowpine on 2009-08-04
Yeah! Glad you got it working. :)

---

