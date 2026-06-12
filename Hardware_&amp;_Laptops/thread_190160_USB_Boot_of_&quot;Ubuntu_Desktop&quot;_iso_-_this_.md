---
title: "USB Boot of &quot;Ubuntu Desktop&quot; iso - this might help"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by ariel on 2006-06-05
Hi,

   My new laptop didn't come with a dvdrom; it is so small that there is no space for it. Also I don't have a usb dvd/cd reader. I thought that having a desktop machine as well, i really didn't need another cdrom; after all, all new machines can boot from USB; I was right, but getting an usb disk to boot the new Dapper installer was way harder than I thought.

    I read tons of threads and tried a lot of strategies including the use some weird HP formatting tool that supposedly does some magic of unknown sort, then using syslinux, installing the mbr, and such and such. None of these worked for me.

    If you have a new machine, you might find the following helpful. This comes from various sources including the knoppix usb boot wiki. It did the trick for me, I could boot Ubuntu 6.06 Desktop CD in both my Laptop and Desktop; your mileage may vary (wildly :-)). It uses the good'ol grub instead of syslinux or isolinux.


> Boot from USB disk with multiple partitions
      Grub method:  {assumes that /dev/sda is your usb disk, sda1 the partition you want to boot from}[INDENT][INDENT]             1) Create the partition in the usb disk as needed:   cfdisk /dev/sda; makeit bootable (boot flag), type 0E (FAT16 LBA)   

2) Format it:             mkdosfs -F 16 -v /dev/sda1

3) Mount the partition    mount /dev/sda1 /mnt

4) To setup Grub to boot from the USB drive, copy Grub's working files, namely, stage1, stage2 etc, to the partition
               mkdir -p /mnt/boot/grub
               cp -r /boot/grub/* /mnt/boot/grub

5) Edit /mnt/boot/grub/device.map and set:
                (hd0) /dev/sda
                (hd1) /dev/sdb
                (hd2) /dev/sdc  

6) grub-install --root-directory=/mnt --no-floppy '(hd0)'             

7) edit /mnt/boot/grub/menu.lst and set:
                default 0
                timeout 5
                color cyan/blue white/blue
                title Ubuntu Installer in sda1
                root        (hd0,0)
                kernel          /casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
                initrd          /casper/initrd.gz
                boot

8 ) Mount your Dapper iso (or just open it with file-roller) can copy the whole thing to the new bootable partition in the usb disk

9) Reboot your box, and in BIOS: ensure that your USB Boot is set to mode: USB-HDD ("Auto" mode worked for me too); reboot
[/INDENT][/INDENT] Hope this helps and saves you some time!

---

