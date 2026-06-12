---
title: "Error messages before boot, system stuck"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Wang Tang on 2009-06-05
Hello everyone,

I'm new to Ubuntu, and although I'm quite capable of learning new things related to PC, I'm really stuck here. I searched Google and this forum, but didn't find anything about this error:

I have Windows 7 RC installed on sda1 of my harddisk. I wanted to install Ubuntu 9.04 on sda2, so I downloaded "netbootin" and loaded the x64 version on my usb drive. When I boot from there, an Ubuntu "splashscreen" appears, but after a while, some console messages show up, including the words: 

res Emask 0x4 (timeout) cmd tag ncq ata2.00 "status: { DRDY }", and loads of hexadecimal numbers (dunno if this helps)

However, after about 2 minutes, it continues to boot, and then I can install Ubuntu from the live system. Installation goes really smooth, no problems here whatsoever. On the next boot, GRUB shows up and I select the first entry, "normal" Ubuntu boot. It starts again with the splashscreen, shows console error messages again, but stops there (I waited for 20 minutes, just to be shure). There are although some other error messages than in the "live" boot, like:

...
ata2.00:  irq_stat 0x44000008
ata2: SError: { Proto TrStaTrns UnrecFIS }
...
ata2.00: status: { DRDY ERR }
ata2.00: error: { ICRC ABRT }


On second try to boot, it gives me a different error, stating:

ALERT! dev/disk/by-uuid/.... does not exist. Dropping to shell.
...


Hardware used is
Acer Aspire 3810T
Intel SU9400 1.4GHz CPU, 64bit
4GB Ram

Is there any way I can resolve this?

---

### Post by avilella on 2009-06-06
Hi Wang Tang,

Can you have a look at the info from other 3810T related threads here?
[https://launchpad.net/~acertimeline](https://launchpad.net/~acertimeline)

Specially, this installation instructions:
[http://ubuntuforums.org/showpost.php?p=7314698&postcount=1](http://ubuntuforums.org/showpost.php?p=7314698&postcount=1)

> **Wang Tang said:**
> Hello everyone,

I'm new to Ubuntu, and although I'm quite capable of learning new things related to PC, I'm really stuck here. I searched Google and this forum, but didn't find anything about this error:

I have Windows 7 RC installed on sda1 of my harddisk. I wanted to install Ubuntu 9.04 on sda2, so I downloaded "netbootin" and loaded the x64 version on my usb drive. When I boot from there, an Ubuntu "splashscreen" appears, but after a while, some console messages show up, including the words: 

res Emask 0x4 (timeout) cmd tag ncq ata2.00 "status: { DRDY }", and loads of hexadecimal numbers (dunno if this helps)

However, after about 2 minutes, it continues to boot, and then I can install Ubuntu from the live system. Installation goes really smooth, no problems here whatsoever. On the next boot, GRUB shows up and I select the first entry, "normal" Ubuntu boot. It starts again with the splashscreen, shows console error messages again, but stops there (I waited for 20 minutes, just to be shure). There are although some other error messages than in the "live" boot, like:

...
ata2.00:  irq_stat 0x44000008
ata2: SError: { Proto TrStaTrns UnrecFIS }
...
ata2.00: status: { DRDY ERR }
ata2.00: error: { ICRC ABRT }


On second try to boot, it gives me a different error, stating:

ALERT! dev/disk/by-uuid/.... does not exist. Dropping to shell.
...


Hardware used is
Acer Aspire 3810T
Intel SU9400 1.4GHz CPU, 64bit
4GB Ram

Is there any way I can resolve this?

---

### Post by Wang Tang on 2009-06-06
Hi avilella,

thanks for your msg and the link to tokyoahead's post, I wonder how I could've missed this thread.
The workaround with libata.noacpi works fine!
I will see for the other things now.

---

