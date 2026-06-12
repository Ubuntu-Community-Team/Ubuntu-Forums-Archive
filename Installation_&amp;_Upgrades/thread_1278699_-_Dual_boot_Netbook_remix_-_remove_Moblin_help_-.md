---
title: "- Dual boot Netbook remix - remove Moblin help -"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by tjc.501 on 2009-09-29
Hi guys,
I recently installed Mobiln on my Aspire One netbook; it is dual booting with xp. Theirs too many bugs still in moblin for my taste and I would like to remove it and install Ubuntu Netbook Remix. When I installed Moblin, I installed grub on the xp partitions mbr. Since their isn't any documentation for installing; I wasn't sure of where to write it. Now, when I install Ubuntu, will it detect xp? Will it write over Moblins grub, which is written to xp's mbr. How should I proceed? I'm trying to avoid a grub nightmare here, any help is greatly appreciated. Thanks in advance.
Tj

---

### Post by danns on 2009-09-29
There is no grub nightmare my friend, grub is beautiful.  Upon installation of Ubuntu it should detect your Windows partition and set up grub accordingly.  The other thing you can do is backup your /boot/grub/menu.lst and use that for reference should it not detect your windows partition and set it up.

Remember, you can very easily boot the installed OS via grub using the command line.  If you read the grub documentation over at [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) you will see how easy it is.  

Never for get, grub is the boot loader of the gods!

---

### Post by tjc.501 on 2009-09-30
> **danns said:**
> There is no grub nightmare my friend, grub is beautiful.  Upon installation of Ubuntu it should detect your Windows partition and set up grub accordingly.  The other thing you can do is backup your /boot/grub/menu.lst and use that for reference should it not detect your windows partition and set it up.

Remember, you can very easily boot the installed OS via grub using the command line.  If you read the grub documentation over at [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) you will see how easy it is.  

Never for get, grub is the boot loader of the gods!

Thanks for the advise. I really appreciate it. I have worked with grub before but I guess I should have mentioned I will be installing 9.10.  I haven't played around with grub 2. Any difference?

---

