---
title: "dsdt: what do I do now?"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-02-15
I need some help here.

I've worked out I need a new DSDT table and I've downloaded the right one. Now, how do I install it so it is recognised and so works?

Any help would be useful.

---

### Post by snop on 2005-02-15
Hi,

I already installed a new dsdt. I just followed instructions at [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

Basicaly you must append your dsdt to initrd. After that you must update your grub configuration (/boot/grub/menu.lst).

Remember to backup all your files. In fact, what I did, copy initrd to something like initrd-dsdt an append my dsdt there. Then added a new entry at menu.lst to update my grub.

Just remeber that everytime you update your kernel you'll have to repeat the process.

That's it.

Bye

PD: Don't forget the -n mentioned in the instructions you'll find! I did at first and it didn't detected my new dsdt.

---

### Post by lerrup on 2005-02-16
thanks for the help, but usr/src/linux doesn't exist, so I where do  I cd to?

I've also never used the patch - is there anything else i need to do to compile?

Thanks

---

### Post by GilGalad on 2005-02-16
The ubuntu kernels are already patched with this patch so you do not need to recompile:

$ cat /boot/config-2.6.10-3-686 | grep ACPI_INITRD
CONFIG_ACPI_INITRD=y

So you just need to follow the instructions "After compiling the kernel"...

Cheers.

---

### Post by lerrup on 2005-02-16
I'm sorry about this but I think I'm missing something here.

I think I've now got an initrd that has been patched, but it seems ignored at boot time.  There is mention of amending grub/menu.lst, but to what?  Should it be to the initrd instead of the initrd [kernel version]?

Thanks again.

---

### Post by GilGalad on 2005-02-17
[QUOTE=lerrup]I'm sorry about this but I think I'm missing something here.

I think I've now got an initrd that has been patched, but it seems ignored at boot time.  There is mention of amending grub/menu.lst, but to what?  Should it be to the initrd instead of the initrd [kernel version]?

Thanks again.[/QUOTE]
 Ok. You have to type (note the inverted quotes):

```
sudo mkinitrd -o /boot/initrd.img-`uname -r`
sudo echo -n "INITRDDSDT123DSDT123" >> /boot/initrd.img-`uname -r`
sudo cat DSDT.aml >> /boot/initrd.img-`uname -r`
```

Once rebooted you should see in the output of "dmesg" something saying that the new DSDT has been found and has been read.

---

### Post by lerrup on 2005-02-17
Unfortunately, there is no such message and of course the power control doesn't work.

I am pretty confident I have followed the insructions but any ideas about what I might have done wrong?

---

### Post by lerrup on 2005-02-18
tahanks for your help, I've just installed Hoary in a fit of madness and this problem has been solved.  I have others, but!

---

