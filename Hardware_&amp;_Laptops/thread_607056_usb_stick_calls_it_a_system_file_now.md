---
title: "usb stick calls it a system file now"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by JermainWijnhard on 2007-11-08
Hi,

I used a usb stick / mp3 player, to move some files, but somehow the stick made 2 directories 'system files', i cant delete them. I can't chmod them in order to delete them and when im in root i can't make any changes to or inside of the directories. Is this a known occurance and is there a solution?

I'm a beginner to the terminal, so keep that in account if you have difficult solutions ^^

---

### Post by samborambo on 2007-11-08
You have to be more specific with the make/model of MP3 player. If you need to get rid of those system files, first find out what name the device is given when it's plugged in.

type:
```

mount
```

You'll see a device mounted in /media folder called 'disk' if the disk label is unnamed. The device name will be something like /dev/sda1. If you've got SATA or SCSI drives in your machine as well the device name will be something like /dev/sdb1 or /dev/sdc1. Make you know which device it is! 

[LIST]
[*]Make you copy all the information you want off the usb stick before going any further.
[*]Now, unmount the device by right-clicking the desktop icon.
[*]This command will flatten the partition, filling it with zeros. You will get no confirmationbefore proceeding! Type (remember to change sda1):
```

sudo dd if=/dev/zero of=/dev/sda1 bs=4096

```
[*]Once that finishes, type:
```

sudo mkfs.vfat /dev/sda1

```
[*]Once that finishes, pull the stick out, plug it back in and a clean drive will appear. 
[/LIST]

---

### Post by JermainWijnhard on 2007-11-09
sudo mkfs.vfat /dev/sda1
mkfs.vat: command not found :(

In addition, it's a 1Gig MPAXX mp3 player USB stick, i don't know the model number.

---

### Post by JermainWijnhard on 2007-11-12
I'm bumping this topic because since i installed Gutsy, the same has occured to my external HD. I cannot remove files or dirs from my ext. HD or USB stick. Please help, I'm getting desperate. :(

---

### Post by Yexo on 2007-11-12
Make sure you type mkfs.vfat and not mkfs.vat. The error you show looks like you types mkfs.vat.

---

### Post by bingoUV on 2007-11-12
```

sudo /sbin/mkfs.vfat /dev/sda1

```

---

### Post by JermainWijnhard on 2007-11-12
thank you for the quick responses. I will try it as soon as i'm at home. (i'm at work totally not refreshing this page,.. really)

---

