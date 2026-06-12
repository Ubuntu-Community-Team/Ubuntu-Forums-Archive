---
title: "Using new compiled DSDT.aml while Booting?"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by zoomingrocket on 2005-07-31
Hello everyone..

I have Acer Aspire 3002NLC Laptop..with Phoenix 3A16 Bios..
As per the details on Acpi.sourceforge.net.. i got the required ASL fle for my BIOS version and compiled using an IASL compiler.

Now.. i have put the DSDT.aml file in /root/

While booting from GRUB.. 
If i pass:  initrd /root/DSDT.aml


It says...  Kernel Panic.. VFS Blah..blah..

Now can you tell me how to pass the DSDT.aml file for booting?
I am using Ubuntu 5.04....
Also.. there is already another: initrd /root/***.img     line
Wat is that?

Please help..so that my Battery Status would be back ON...
I am already fedup with so many compilations and stuff done...

Just struck at the final step!
Thanks in advance..

Regards,
Zooom..!!

---

### Post by luca_linux on 2005-07-31
```

echo -n "INITRDDSDT123DSDT123" >> /boot/initrd.img-{version}-dsdt
cat DSDT.aml >> /boot/initrd.img-{version}-dsdt
echo -n "INITRDDSDT321DSDT321" >> /boot/initrd.img-{version}-dsdt

```

---

### Post by zoomingrocket on 2005-07-31
Currently i have following in my menu.lst file in /boot/grub/

```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

```

What change should i make exactly??
Sorry i am newbie ;)

Thanks...

Regards,
Zooom..!!

---

### Post by zoomingrocket on 2005-08-01
[QUOTE=zoomingrocket]Currently i have following in my menu.lst file in /boot/grub/

```

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

```

What change should i make exactly??
Sorry i am newbie ;)

Thanks...

Regards,
Zooom..!![/QUOTE]
 Any help???

Please!



EDIT  EDIT:
Found my answer at:  [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)


Thanks

---

