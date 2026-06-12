---
title: "Using a HDD when launching off of a USB"
date: 2018-03-01
forum: Hardware
---

### Post by thescriptergeek on 2018-03-01
Basically I put Ubuntu on a USB stick(16GB) so I can boot off of multiple computers using it easily. There is a laptop that I use it on a lot, I was wondering if I could use spare HDD space I have on it. Also sorry if this is on the wrong thread, this is my first post ever

---

### Post by droid2bsd88 on 2018-03-03
Yoyu're stated goal is rather vague, from my experience I know that if you get either the cd/dvd iso image or a memstick img file you shoild be able to  use thelater image file to boot directly into a x11 based installer and  as far as a second hard drive you would have to check if the  manufacturer of you're deisred laptop sells a replacement caddy for the laptop cd drive that whould  be you're method for mounting you're second hdd or sdd in aforementioned laptop. The aforementioned expansion bay  caddies are useraslly only available for workstati=on replacement type laptop and not the typical consumer laptops. As for duel booting once you haveyou're second hard disk drive or ssd  mounted in the laptop in question you could devote the decond fixed disk drive to Linux which would allow you to duel boot linux and windows via chain loading  windows with grim on the primary (/dev/sda) boot sector and pointing  grub to /dev/sdbX where x is you're ubuntu (Linux) /boot partiton on the secondary fixed disk drive.

---

### Post by kenogo2 on 2018-03-03
So if I understood you correctly, you want to use the internal SSD in your laptop as an additional storage for your Ubuntu installation. This is very much possible, but you need to be careful and backup your entire hard drive first! Probably, nothing bad is going to happen, but you never know! You can make a backup from Ubuntu in the following way:

1. Boot Ubuntu from your USB stick
2. Connect an external hard drive
3. Open a terminal
4. Run ```
sudo fdisk -l
``` to determine your hard drive's names. Most likely, it's gonna be /dev/sda for your internal SSD and /dev/sdc for your external hard drive, but you need to check yourself! I'll just assume it's /dev/sda for internal and /dev/sdc for the external in the following steps.
5. Make sure your external hard drive is not mounted (If it appears on the desktop, right click it and select "unmount")
6. Run ```
dd if=/dev/sda of=/dev/sdc
``` and just WAIT! This will take pretty long, possibly a day, and it produces no output! So just wait it out.

After dd is done running, you'll have a backup if your SSD that you can restore in case anything is wrong. This means you're now ready to use gparted to create a new partition that you'll use for Ubuntu. If gparted isn't installed, you can install it with ```
sudo apt install gparted
``` Gparted should be pretty self-explanatory.

---

### Post by sudodus on 2018-03-04
You can have a persistent live or installed system in a USB drive (and it can be a HDD in an external box). See the following links,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Persistent live:

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Installed system:

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by C.S.Cameron on 2018-03-04
My wife always boots off an external USB drive so that she can plug it into whatever is convenient when we travel.
This year we set up her home computer with Ubuntu installed on a fast SSD.
When the external is plugged in, the computer uses the home partition from the external.
The experience is just like booting off the external drive, with all her stuff on it, except much faster.
The home computer needs to have the same programs installed as the portable drive.
The path to the external drive's home partition, (UUID), needs to be listed in the home computers fstab.
User names etc must also be the same on the internal and external drives.

---

