---
title: "HP nx7400 laptop dual boot Kubuntu edgy with WinXP issue"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by kkm1978 on 2006-11-15
Installed Kubuntu 6.10 edgy on my HP nx7400 after creating a new partition.

Kubuntu worked very well and GRUB boot loader correctly configures the Win XP boot option.

But, if I log on to WinXP - it goes to recovery mode reinstalls WinXP again ( Also Kubuntu is lost and previous WinXP as well )

I can't give up WinXP for the moment as I need it for some applications.

Please advice on how to configure this laptop with dual boot option.

[COLOR="DarkRed"]System:
HP nx7400
T2300 Inter Core Duo
512 MB RAM
60GB Hard Drive[/COLOR]

---

### Post by altaaa on 2006-11-16
The Ubuntu installer probably sees your recovery partition as a Windows XP partition.

I bet it's possible to edit your /boot/grub/menu.lst to boot from your actual Windows partition, but I don't have enough knowledge to show you how.

However, I would manually reinstall the notebook with Windows and then Ubuntu. While installing Windows I would completely remove all partitions that are on the hdd, including the restore partition. Make sure you have restore CD's, though.

---

### Post by kkm1978 on 2006-11-17
Thanks Altaa.

Let me check that again !
:cool:

---

