---
title: "How to reformat a memory stick?"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by YourSurrogateGod on 2006-01-26
Ok, I don't know what I did exactly to it, but it seems that all of the data that I had on my memory stick became corrupted and some parts of it is unreadable. Fortunately, this is not  massive loss for me... it's something that I can easily deal with. Now. What I'd like to know is how can I reformat or restore (for lack of a better word) that memory stick? I'd like to be able to use it from time to time.

I tried disks in system, but the button that said "reformat" was inactive/greyed out, which meant that I couldn't use it.

Here's what I got when I did lsusb:
```
Bus 005 Device 005: ID 0d49:3100 Maxtor
Bus 005 Device 003: ID 08ec:0845 M-Systems Flash Disk Pioneers
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:0904 Hewlett-Packard DeskJet 845c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

---

### Post by BenTyreman on 2006-01-26
Last time I formatted my flashpen, I did it using the console.

```
mount
```
to find what the pen is called (typically /dev/sda1), unless you have SATA hard drives, in which case it would be /dev/sdb1, etc.

```
sudo umount /dev/sda1
```
as the format procedure only works on unmounted devices.

```
sudo mkfs.vfat -F 32 /dev/sda1
```
replacing sda1 with whatever your system calls is.

Alternatively, to format with FAT16 instead of FAT32, use
```
sudo mkfs.vfat -F 16 /dev/sda1
```

---

### Post by YourSurrogateGod on 2006-01-26
Thanks, that did the trick.

---

### Post by Sporkman on 2007-12-10
Works great on my SD memory card - thanks!

---

