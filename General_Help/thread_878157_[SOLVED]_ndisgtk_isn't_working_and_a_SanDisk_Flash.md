---
title: "[SOLVED] ndisgtk isn't working and a SanDisk Flash Drive"
date: 2008-08-02
forum: General Help
---

### Post by Newuser1111 on 2008-08-02
(The desktop computer, not my laptop.)

ndisgtk isn't working.
Or is there a better way to get a NetGear WG111T to work?


A SanDisk Cruzer Micro 2.0 GB also isn't working.


A USB Numeric Keypad also isn't working.



I think the USB ports might not be working.(All three things are USB. Except the program) So how do I fix that?

---

### Post by rEbyTer on 2008-08-02
I need more information. So when you insert your USB thumb drive in computer type:
```
$ sudo fdisk -l
```
And tell me what you see.

Also it is VERY important to copy paste the output of:
```
lsusb
```

---

### Post by Newuser1111 on 2008-08-02
```
$ sudo fdisk -l
```
Disk /dev/sda:40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd560d560

Device Boot    Start    End    Blocks    ID   System
/dev/sda1 *        1    272   2184808+    b   W95 FAT32
/dev/sda2        273    2515 18016897+    c   W95 FAT32 (LBA)
/dev/sda3       2516    4607 16803990    83   Linux
/dev/sda4       4608    4865  2072385    82   Linux swap / Solaris

```
lsusb
```
Doesn't show anything.

---

### Post by rEbyTer on 2008-08-02
try
```
sudo lsusb
```

If this doesn't show anything it may **SEEM** that [COLOR="Red"]your USB ports are not working properly[/COLOR].

For example mine shows this:
```
Bus 005 Device 005: ID eb1a:2761 eMPIA Technology, Inc. 
Bus 005 Device 004: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0566:3004 Monterey International Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 001 Device 001: ID 0000:0000  
```

*Monterey* is my keyboard, *Intelli* is my mouse. *kingston* is internal card reader and *eMPIA Technology, Inc.* is my internal web camera.

If **lsusb** doesn't report anything there are serious problems with your usb ports.

---

### Post by Newuser1111 on 2008-08-02
Still shows nothing.

But I dont think it ever finishes.
```

djk@djk-desktop:~$ sudo lsusb
[sudo] password for djk:
Sorry, try again.
[sudo] password for djk:


```


EDIT:
Nevermind,
Restarting the computer fixed all of those problems.

---

