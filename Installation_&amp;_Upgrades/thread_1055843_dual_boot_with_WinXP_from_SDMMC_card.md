---
title: "dual boot with WinXP from SD/MMC card"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by csarlee on 2009-01-31
Hello All,

I have a HP EliteBook 9630 laptop with WinXP. It has plenty of free space on its hdd so I want to install Ubuntu but in a tricky way. As it is a company laptop, I don't want to install it next to the XP. I can create partitions to it but as the lappy has built-in SD/MMC cardreader I am thinking of booting from the card. Of course it is capable of booting from SD/MMC card I checked in the BIOS. So I want to have a config like if the card is plugged in, the laptop boots from there and loads Ubuntu (which is on the hdd!) and when there is no memocard it boots and loads WinXP.
I think, it can be done if I install Ubuntu normally then make a card bootable and install GRUB on the card and set it up to boot Ubuntu from the hdd. But what happens if there is no card? Do I need to remove GRUB from Ubuntu but keep that partition bootable? And when it boots without card it will find the XP bootloader?

Sorry for the length...

Csarlee

---

### Post by meindian523 on 2009-01-31
AFAIK,that is not possible.Even when Ubuntu is installed on an external HDD(just another form of external storage),Grub has to be put on the internal HDD,because when booting Ubuntu,you plug in the external HDD,and it boots fine,while when booting other OSs,you don't need the external HDD.In this case with the external HDD unplugged,selecting Ubuntu will give you error 15.

Grub takes over the booting process from the Windows bootloader when you install a Linux distro and chainloads it.Your scheme could be realized by using Wubi,thus you get a (pseudo) dual boot,but that doesn't use your MMC card.Windows' bootloader will boot both Windows and the Wubi install of Ubuntu.

---

### Post by meindian523 on 2009-01-31
That said,your scheme is quite interesting,and if it does ever get solved,I would love to try it out on a cell phone or something similar.The only barrier would be whether said phone would boot from a memory card.

---

