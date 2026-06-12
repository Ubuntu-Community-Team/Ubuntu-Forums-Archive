---
title: "Boot from a flash drive / external USB drive"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by kwilliam on 2009-08-28
I'm trying to make a bootable flash drive so I can test other Linux distributions without partitioning my already crowded laptop hard drive. I've been trying to install Chakra (based on Arch Linux) to the flash drive, but haven't figured out how to make it boot successfully. Since I'm test driving the distro, I'd prefer a normal install than the funky "Live CD with persistent memory" trick that's all the buzz lately. Only I'm a little confused... some instructions say to install GRUB, others say to use Syslinux, I think I need a kernel that supports booting from USB, etc.

So what I've currently got is a 8 GB flash drive partitioned thus:
```
/dev/sdb1 ext2       1.0GB  /boot
/dev/sdb2 linux-swap 275MB
/dev/sdb3 ext3       6.25GB /
```

I installed GRUB to /dev/sdb. When I try to boot from the flash drive GRUB runs fine I think, but sometime after the "Loading vmlinuz......" it craps out saying it can't find /dev/sda or init was killed prematurely or something. (I forget the exact message.)

Anyway, my question is, what is the CORRECT way of doing this? Should I have made /boot FAT-32 and used syslinux, or do I just need to compile a different kernel to get it to boot from USB or what is the requirements to install Linux on an external USB drive?

---

### Post by Jordii on 2009-08-28
This might help: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by Jordii on 2009-08-28
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Mighty_Joe on 2009-08-28
You can install Ubuntu to a flash drive just like any other drive, and the Ubuntu installer will install Grub for you.  Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680"), which has some configuration hints to help mitigate wear on the flash drive.

---

### Post by clancymf on 2009-08-28
My question is how do you get it back to its factory format, or so the USB stick can be usable again.

Update - Never mind... unmounted and used gparted.

---

### Post by kwilliam on 2009-08-29
Hey thanks for the links, they'll definately come in handy. Unetbootin looks neat.

---

### Post by kwilliam on 2009-08-29
> **Mighty_Joe said:**
> You can install Ubuntu to a flash drive just like any other drive, and the Ubuntu installer will install Grub for you.  Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680"), which has some configuration hints to help mitigate wear on the flash drive.

So it turns out the reason it wouldn't boot is my grub menu.lst file specified root=/dev/sda3. I was going on the assumption that when booting from the USB drive, that would become the first hard drive. However, actually it stayed /dev/sdb! Is that normal or is that a quirk with my laptop? Anyway, changing root=/dev/sdb3 allowed it to boot. (Actually, I used root=UUID= first, and then once that worked I did df -h and saw root was mounted on /dev/sdb3.)

I'll look into the wear mitigation stuff though, thanks.

---

