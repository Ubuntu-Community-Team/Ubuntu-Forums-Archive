---
title: "Flash Drive"
date: 2010-07-25
forum: Hardware
---

### Post by Denicia on 2010-07-25
Help please, my flash drive is not showing up on ubuntu.

---

### Post by lykeion on 2010-07-25
See _[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)_

---

### Post by Denicia on 2010-07-25
Thanks lykeion. I have a dual boot system and i have two windows partition that are NTFS. In the list three NTFS partitions are showing up but i'm not sure which one is my flash drive.

---

### Post by lykeion on 2010-07-25
Is it a USB stick flash frive you have? If so, they are usually Fat16 or FAT32

Does **sudo fdisk -l** output any FAT16/FAT32 drive?

Does **lsusb** output any line with your Flash stick mentioned?

---

### Post by Denicia on 2010-07-25
There's no FAT showing up and the light from my flash drive goes out right after i plug it in. Its a sandisk drive.

---

### Post by lykeion on 2010-07-25
Does **lsmod | grep usb_storage** show a line?
If not, try **sudo modprobe usb_storage** and then try again.

You should also check dmesg like this:
Open a terminal and enter **dmesg | tail**
Plugin your stick and wait a while, then enter **dmesg | tail** again
Does it output that usb-storage found any device?

A third thing you can do is to try another USB port (it's not uncommon that they are faulty)

---

