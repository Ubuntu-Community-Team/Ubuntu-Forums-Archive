---
title: "HardDiskTrouble"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by leonoel on 2008-12-16
We just got new Dell Computers in the laboratory, and I tried to install ubuntu.

I kept facing the following message when trying to install from the live CD (Ubuntu 8.04)

ata2.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata2.00 cmd a0/00:00:00:24...
ata2.00 status {DRDY}

That message over and over, after a while I got tired and rebooted using windows, I did a disk check and tried again, this time It actually let me install, but when I try to run ubuntu it shows the same messages. 

I have checked some topics and it seems to be a common issue, is there any solution other than opening the CPU and voiding my warranty.

Thank You

Leon

---

### Post by Partyboi2 on 2008-12-16
Have you tried using irqpoll as a boot option, it has worked for others. To add the boot option press ESC when you see grub loading..... then highlight the kernel you boot into and press "e" to edit then hightlight the line starting with "Kernel" and press "e" again then add ```
irqpoll
``` then press "enter" then "b" to boot. If this allows you to boot Ubuntu you will need to add it to your grub menu.lst to make it permanent.

---

### Post by leonoel on 2008-12-16
> **Partyboi2 said:**
> Have you tried using irqpoll as a boot option, it has worked for others. To add the boot option press ESC when you see grub loading..... then highlight the kernel you boot into and press "e" to edit then hightlight the line starting with "Kernel" and press "e" again then add ```
irqpoll
``` then press "enter" then "b" to boot. If this allows you to boot Ubuntu you will need to add it to your grub menu.lst to make it permanent.

Hey

Thank You very much it was a great deal of help.

Is there a link where they explain that option,  or what does it mean, just out of curiosity

Thanks Again

---

### Post by Partyboi2 on 2008-12-16
>  irqpoll 
    Changes the way the kernel handles interrupt calls (set it to[COLOR=Blue] [polling]("http://en.wikipedia.org/wiki/Asynchronous_I/O")[/COLOR]). Can be useful in case of hardware interrupt issues. 

I am assuming by your reply that it worked? If it did work then you will need to add it to your /boot/grub/menu.lst if you have not already done so. You can follow [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation")

---

