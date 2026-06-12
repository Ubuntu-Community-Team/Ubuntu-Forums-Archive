---
title: "instalation problems"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by RuanLopesBrazil on 2009-01-06
[B]I tried to install ubuntu, but when I do the boot an error message on screen

"error reading boot cd"

someone help me

thank you[/B]

---

### Post by Pumalite on 2009-01-06
Use good quality CD-R. Do not use CD-RW. Do md5sum on the iso, burn at 4x or less. Burn as 'image' ('iso')
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by RuanLopesBrazil on 2009-01-06
[B]I used cd-r of good quality, recorded at 4x, as recorded image.
but the error still![/B]

help me 
thank

---

### Post by dbqp on 2009-01-06
> **RuanLopesBrazil said:**
> [B]I used cd-r of good quality, recorded at 4x, as recorded image.
but the error still![/B]

help me 
thank

Have you tried the Alternate Install Disk? See:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It's text based, but you should be able to just accept the default prompts (except user name, computer name, password, etc...)

This disk has saved me many times on various computers where the Live CD would not install.

Also, you should try to limit your problems on one issue to one thread. You have another posted [here]("http://ubuntuforums.org/showthread.php?t=1032287") which you have the same problem.

Also, make sure you have created the CD as an ISO bootable...

---

### Post by RuanLopesBrazil on 2009-01-06
[B]thanks for the tip
I will try here, and if you do not have success
I will post again[/B]

---

### Post by RuanLopesBrazil on 2009-01-06
[B]someone can diser me what I type
in boot
if I press the f6
to install
this may be a problem of wrong boot

thanks[/B]

---

### Post by Pumalite on 2009-01-06
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html) 
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html) 
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes) 
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11) 
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317

---

