---
title: "Problems booting xp without external hard drive"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Drex89 on 2007-10-31
I have XP installed on my laptop. I installed Ubuntu Feisty Fawn on my external hard drive. It worked fine, but in order to boot Ubuntu I would have to go into my BIOS and set it to boot from my external hdd. This wasn't a huge problem, just a minor annoyance. When I upgraded to Gutsy, I get the boot menu where I can choose between Gutsy, XP, or a few other Gutsy options. Unfortunately, when I took my laptop to class the other day(without the external hard drive obviously) I found that I can't boot my computer without the ext hdd. How can I fix this problem? (Without messing with partitioning anything. I don't want to lose any data from either hdd.)

---

### Post by Bliepo32 on 2007-10-31
Well, GRUB installs itself to the Master Boot Record (MBR). It also install itself into your external hdd in /boot/grub. When a computer boots, it first reads the MBR. Then it uses the instructions in there. Your MBR tells it to execute GRUB, which is on your external hdd (so it is not found).

Unfortunately for you, the only way to fix it, is to make a partition on your normal hdd, and make a samll /boot partition.

EDIT:
I just thought of another way which **might** work. You could use a USB-stick, format it as FAT-16, and use that as /boot partition. This does has one major consequence though: you need your USB if you want to boot.

And I thought of another method: use the SuperGRUB disk. That way, you can boot Windows without your external hdd.

---

### Post by Drex89 on 2007-11-01
Wow thanks. I didn't want to mess up my data, so I went with the SuperGRUB disc. That is awesome! It did exactly what I needed without messing anything up. Thanks for your help!

---

