---
title: "Problem with an external hd"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by craig88 on 2008-01-16
hi,just wondering if any one can guide me here its not so much a problem as a query.
basically linux is asking me to "mount" my external hdd if i mounted it would this delete the data on the hard drive ?

---

### Post by dgray_from_dc on 2008-01-16
No. Mounting a drive just makes it available for use.  It won't hurt a thing.

---

### Post by craig88 on 2008-01-16
brilliant, thanks for the quick help

---

### Post by craig88 on 2008-01-17
how do i mount the drive i right clicked and pressed mount but it said i should try a force mount? is there something to type into the terminal or something im pretty new to all this lol

---

### Post by dgray_from_dc on 2008-01-17
Sometimes you need admin rights to mount a disk.  (I'm not sure why)  Try using the following.

```
sudo mount /dev/sd_1
```

Where the blank will vary depending on where your disk is assigned.  For instance, my PC has only a single harddrive and a cd-rom.  So, for me my first hard drive is /dev/sda and my cd-rom is /dev/sdb and an additional disk would automatically be assigned to /dev/sdc.  So, I would use

```
sudo mount /dev/sd[COLOR="Blue"]**c**[/COLOR]1
```

This stands for mount sdc partition number 1.  (I assume that your external hd has only one partition)

---

### Post by craig88 on 2008-01-17
Thanks i see to be on the right track now I found my ext to be sdb1 so i type the code in exactly as you put it and it says this: 

*****@*****laptop:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

so i decided to see if i could find them myself and neither file exists?

---

### Post by dgray_from_dc on 2008-01-17
That error happened because Linux didn't have any info on your disk, what it was and where you wanted to mount it.

Try this one

```
sudo mkdir /media/usbdisk
sudo mount -t vfat /dev/sdb1 /media/usbdisk 
```

The first line creates a mountpoint [COLOR="Blue"]usbdisk[/COLOR] in your /media directory.  (It may already be there, in that case don't worry.)

The second elaborates on the mount command.  It tells Linux that the disk is FAT16 or 32 and to place your data in the directory you just created.

P.S. if the partition is NTFS then replace vfat with ntfs in the second line.

---

### Post by theophile on 2008-01-17
Shouldn't lvm be handling this?

---

### Post by dgray_from_dc on 2008-01-17
I don't know, I don't know all of the ins and outs of LVM.  I've been using Linux on and off since '98 so I'm relatively good and some of the older standards but LVM is very new to me.

---

### Post by craig88 on 2008-01-17
whats lvm? and i tried that code it said only root can do that so sounds like i just have to login as root and run the code

---

### Post by theophile on 2008-01-17
Linux Volume Manager is supposed to automagically handle mounting and removal of remote media. For something as common as usb mass storage devices such as an external HD, you should just be able to plug it in and an icon should appear on your desktop. When you plug it in, what is the output of dmesg?

---

### Post by craig88 on 2008-01-17
i can see it but just cant access what dmesg?  soz i  installed linux for the first time on monday im still very new

---

### Post by craig88 on 2008-01-17
p.s do u have to install linux volume manager?

---

### Post by dgray_from_dc on 2008-01-18
You shouldn't, it's part of the default install.

---

### Post by craig88 on 2008-01-18
its ok i sorted it now any thanks for the help it was much apreciated

---

