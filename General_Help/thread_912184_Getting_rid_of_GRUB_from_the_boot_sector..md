---
title: "Getting rid of GRUB from the boot sector."
date: 2008-09-06
forum: General Help
---

### Post by chrispche on 2008-09-06
Can anyone help with the following problem. I myself use Ubuntu. However on my fathers Sony Vaio Laptop he wants vista gone and XP installed. I have booted into Ubuntu on the live CD and deleted the NTFS partitions with gparted on the Live CD. However due to having to backup info from one hard drive to another. I had to install Ubuntu and copy from one HDD to another HDD and then back again. You really don't need to know the details of that.

The problem occurs when I try to install Windows XP, it says there is no hard drives to install to. However, Ubuntu and Vista see the hard drives. Why not XP?

Is this because GRUB is installed? If so, if I boot up into a Live CD what command can I use in the terminal to remove GRUB from the boot sector?

Cheers.

---

### Post by da.tiger on 2008-09-06
its because your laptop is SATA based, and xp doesnt come with the relevant sata drivers. Download the sata drivers from your manufacturer and use nlite [http://www.nliteos.com/](http://www.nliteos.com/) to build your own custom xp. 

pm me if u want a step by step tutorial how to nlite an xp installation and i ll write one for yoU :)

cant post it here, because it isnt relevant to ubuntu :)

it should be fixed

da.tiger

PS.. After the xp installation, u ll actually have to restore grub.

---

### Post by chrispche on 2008-09-06
I PM'ed you. Just a quick note to let you know. I don't have access to a running windows machine only Ubuntu. So I can't run nLite. I'll download the manufacturers drivers to my Ubuntu machine.

---

### Post by cooke77 on 2008-09-06
When you deleted those NTFS partitions...you also destroyed the 'Dual-Boot' Grub.
So that, now, Ubuntu 'sees' itself as 'First Preference'. 
(Albeit, that the whole hard-drive is also now ex3....completely.)
Only way around this, is............a complete Re-Install.
With XP. (First.)
Then, Ubuntu (Installed 'within Windows'.)..........on the NTFS 'format'.

---

