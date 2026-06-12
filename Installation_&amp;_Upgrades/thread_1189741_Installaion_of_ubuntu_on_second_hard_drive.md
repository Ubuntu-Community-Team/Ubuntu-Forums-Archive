---
title: "Installaion of ubuntu on second hard drive"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by santiago87 on 2009-06-17
Hi, I have two hard disks on my computer, an 80GB drive and a 40GB drive. I installed windows xp on the 80GB drive, then installed ubuntu 8.10 on the 40GB disk. For ubuntu I used automatic installation, and used the whole drive. Ubuntu was installed correctly and worked well, but when it restarted I had no GRUB to choose which OS I wanted to boot from. When I tried to boot from the 80GB disk using the boot menu from the bios i received a message: ;RPL HALTED, i don´t know what i did wrong. From ubutu i can see that the 80GB disk, still contains my windows folders and files.
Thank you for your help

---

### Post by brncao on 2009-06-17
I believe Grub was installed on your second hard drive. Ok boot up using the LiveCD. I'm assuming Ubuntu is installed on /dev/sdb1 or (hd1,0). Type the following in the terminal to direct the MBR to Grub.

grub
root (hd1,0)
setup (hd0)
quit

You should see the grub bootloader upon reboot. You should see Ubuntu, but I'm not sure about Windows. If you can't see Windows, then more configurations need to be done.

---

### Post by santiago87 on 2009-06-19
Thanks, but I couldn´t do it, when i inserted root (hd1,0) on the terminal it said that the disk does not exist

---

### Post by coffeecat on 2009-06-19
> **santiago87 said:**
> Thanks, but I couldn´t do it, when i inserted root (hd1,0) on the terminal it said that the disk does not exist

Curious, because even if (hd1,0) (=sdb1) isn't your Ubuntu root partition, there should be an sdb1 since Ubuntu is seeing both discs - according to your first post.

Let's clarify a few things. Are the 80gb and 40gb drives ide or sata? If ide which is master and which is slave? If sata, which sata connectors are each plugged into? Also - which disc is the BIOS configured to boot up from first.

Now boot up into Ubuntu and post the following:

1 - the contents of /boot/grub/menu.lst

2 - the terminal output of:

```
sudo fdisk -l
```

---

