---
title: "Reboot and select proper boot device"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Biopyro on 2009-08-04
I just built a new PC and am looking to use linux for the first time. I have a 20GB HDD which I'm looking to install ubuntu onto, but when I go to boot from it, I just get the "ubuntu reboot and select proper boot device" error. It used to have windows 2000 on it, and it started to boot that fine (I interrupted it and then wiped it), but it doesn't even start booting ubuntu.

It booted fine off the live CD, and I have tried with another HDD also, but got the exact same result.
Is it a problem because the HDDs are old or something else. Most of all - can I fix it?!

It's an IDE drive and is set as master. There are no other HDDs connected and the files (linux files) installed on the drive can be seen and accessed from the live OS.

---

### Post by ajgreeny on 2009-08-04
With the live CD run ```
sudo fdisk -l
sudo blkid
```then navigate to your installed ubuntu's /boot/grub/menu.lst file and copy the bottom, menu part of that, just to ensure that grub is looking in the right place.

---

### Post by Biopyro on 2009-08-04
[FONT=monospace]fdisk
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe438e438

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 1002 MB, 1002438656 bytes
16 heads, 32 sectors/track, 3824 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824      978928    e  W95 FAT16 (LBA)

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="44a7c022-cb69-4471-be5b-2f860b8cd970" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="UDISK 2.0" UUID="98F1-5B1C" TYPE="vfat" 


Also, my mouse cursor freezes occasionally, particularly when the PC is working hard. It doesn't catch up with the movement after it reconnects, but stays still where it was until you move it. Is this just because it's a CD OS? It doesn't do it on my old windows PC.


Is this what you need from the menu.lst file?
# ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9d3cf89d-2950-4f85-b4ef-2988aae3d245
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9d3cf89d-2950-4f85-b4ef-2988aae3d245 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9d3cf89d-2950-4f85-b4ef-2988aae3d245
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9d3cf89d-2950-4f85-b4ef-2988aae3d245 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9d3cf89d-2950-4f85-b4ef-2988aae3d245
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[/FONT]

---

### Post by ajgreeny on 2009-08-04
Sorry, but it looks as if you have ubuntu on sda1 as expected, but for some reason it does not show in the blkid command output. I suppose that could be something to do with the fact that you are running from a live CD, but I don't see why it would not see other unmounted and mounted partitions in the same way that an installed ubuntu system would.  Can you see the sda1 OK in gparted run from the live CD?

PS: That was the right bit of the menu.lst file, but we don't have the UUID of sda1 to check that it is correctly pointing to sda1.

---

### Post by Biopyro on 2009-08-04
Yep, can see it fine in gparted, 2.3gb used, 15.5gb free. Is that what I need to be able to see? There are other bits there too but it says sda1 and suggests to me it's well visible.

---

### Post by ajgreeny on 2009-08-04
OK, using the live CD go to the installed ubuntu menu.lst make a backup copy and then edit the second line in the stanza for ubuntu from ```
uuid        9d3cf89d-2950-4f85-b4ef-2988aae3d245
```to ```
root (hd0,0)
```and in the third line change the same thing half way along to ```
/dev/sda1
```.  The stanza for ubuntu should now read
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```
Now try booting again and let's see if it helps.

---

### Post by Biopyro on 2009-08-04
Says I don't have permissions to save the file.
How do I make sure I have write permission for the HDD from the live CD OS

Edit: it seems I need to know the username of the livecd to change the HDD access permissions. Anyone know what it is?
It just says invalid user for things like ubuntu and livecd

---

### Post by nothingspecial on 2009-08-05
First you need to mount your ubuntu to the live disk.
```

sudo mkdir /ubuntu
```

```

sudo mount -t ext3 /dev/sda1 /ubuntu
```
```


sudo nano /ubuntu/boot/grub/menu.lst
```

Make your alterations then press Ctrl+O to save, Return to confirm and Ctrl+X to exit.

---

### Post by Biopyro on 2009-08-05
Nope, It did allow me to change menu.lst, but still gives me the reboot and select proper boot device error when I try to boot from the hard drive.

---

### Post by Biopyro on 2009-08-05
Looks like it was a problem with the motherboard booting from an IDE drive (ASUS M4N78 ). Loaded ubuntu onto my SATA HDD and went so smooth it's lovely. I don't want it on there so I will have to get a new sata drive, but at least I know the problem now!

---

