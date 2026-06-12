---
title: "Toshiba Bios and GRUB Problems"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Junk_head on 2007-06-27
Hello all, i havent been on ubuntu forums so recently due to your guys work on doing such a good job with this OS, that is until i got a new laptop. 
I got a toshiba tecra a8 and decided to dual boot ubti and vista together. This worked out miraculously from your detailed instructions down here, but a problem arised, unfortunately. As soon as i rebooted the toshiba boot screen would lock and freeze and the toshiba logo would breakup like an nes game gone wrong. Sometimes after a restart GRUB would come on, instead of the toshiba boot menu, im out of ideas ik tried installing Easy bcd but that didnt work either. One more thing i noticed is how long it take ubuntu to boot on the laptop, which takes a lot longer than my elder pc.

---

### Post by Tachyon_ on 2007-06-27
If your laptop freezes to the manufacturer logo BEFORE the grub load's that might indicate a hardware problem.

About the boot time issue. You can do lots of tuning to speed it up by disabling unwanted services and stuff. Lot's of guides are among the first links when searching google for "ubuntu speed boot".
However, if your new laptop is much more high end, that might indicate a hardware problem or hardware detection problem within the linux kernel. I had PCI errors in my new laptop that made the boot freeze for 30 seconds. The boot file is /var/log/dmes, you can view that by typing cat /var/log/dmesg in terminal. Also, if you'd like to see the detailed process during boot and see possible freeze, opening /boot/grub/menu.lst in superuser (sudo gedit /boot/grub/menu.lst) and taking off the "quiet" and splash option enables that. For example:
```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=229017dc-4a54-4492-96d9-766928ab5c5b ro quiet splash

```
If the toshiba logo problem comes before grub loads, I'd say go for a warranty if you have one.

---

### Post by aargus on 2008-05-13
I encountered the exact same problem on Toshiba Tecra A8 EZ-8412 with manufacturer logo and grub.  When manufacturer logo freezes and becomes like a nes game, in reality the grub menu is there because I've been using the up and down arrows to access the other operating system blindly (just by knowing how many times I have to press the down arrow to get to it in the menu and press Enter).

My problem is intermittent though.  At times I see the grub menu normally without modifying anything in Ubuntu or so.  It just happens.  

I'm not sure its a hardware problem.

---

