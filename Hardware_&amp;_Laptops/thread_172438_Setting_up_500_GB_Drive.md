---
title: "Setting up 500 GB Drive"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by DiGiTY on 2006-05-08
I want to install my FAT32 formatted 500 GB ATA/133 hard drive in my linux box to make a home file/media server. I hear my BIOS already supports 48 bit LBA drives, so what do I need to do to get it to work on the Linux/OS end???

I'll be using the latest version of Ubuntu 6.

TIA

---

### Post by zerhacke on 2006-05-08
--Edited--

---

### Post by DiGiTY on 2006-05-09
now will the drive mount automatically when added (after installation) or do I have to tweak the kernel or something to get it to support 48 bit LBA drives?

TIA

---

### Post by Technoviking on 2006-05-09
Please take a more civil tone in this thread or I'm jailing it.

Mike

---

### Post by zerhacke on 2006-05-09
[QUOTE=DiGiTY]I want to install my FAT32 formatted 500 GB ATA/133 hard drive in my linux box to make a home file/media server. I hear my BIOS already supports 48 bit LBA drives, so what do I need to do to get it to work on the Linux/OS end???

I'll be using the latest version of Ubuntu 6.

TIA[/QUOTE]
Since it's already formatted, you won't have to worry about that.  Assuming you want to mount it to /mnt/fat, it's the second hard drive on your computer, and it only has one partition, the command goes like this.

In a terminal, type```
sudo mkdir /mnt/fat (press enter)
mount -t vfat /dev/hdb1 /mnt/fat(press enter)
```

A little explanation: /dev/hdb is the second hard drive.  Drives are numbered a-z, with the first drive on the first IDE chain being hda.  Second drive, primary IDE is hdb.  First drive, secondary IDE is hdc, second drive on the secondary IDE is hdd.

hdb1 is the first partition on the slave drive on the first ide chain.  I'm assuming your Fat32 drive is the slave (secondary) drive on the primary IDE chain.  Change as needed for your setup.

Since you said your drive is already formatted, the -t vfat switch tells the mount command that it's fat32.  If your drive was NTFS, you would have used -t ntfs.

Giving the mount command at every boot is going to be a pain in the ***.  There's a way you can get it to mount automatically at every boot.  Do the following to make that happen, assuming you havn't made the /mnt/fat folder yet.

```
sudo mkdir /mnt/fat (press enter)
sudo cp /etc/fstab /etc/fstab_backup (press enter)
sudo gedit /etc/fstab (press enter)
```

This will make the folder for you, make a backup of the fstab file, and then open gedit the text editor with the fstab file displayed.

In the fstab file, add the following to the last line.  I don't remember if you need to leave a new line at the end of the file, but it couldn't hurt.

```
/dev/hdb1       /mnt/fat  vfat    iocharset=utf8,umask=000   0       0
```

Change as needed as appropriate for your setup.  Remember to press enter after the last line to make the new line.

Once you have that entered into your fstab file, save, close, and open a terminal.  Enter ```
mount -a
``` and hit enter.  Your fat drive will be mounted to /mnt/fat.

---

