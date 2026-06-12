---
title: "Maxtor one touch don't mount"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by Klarsin on 2006-12-09
My Maxtor one-thouch HD won't mount. It is plugged in. I have it hooked up to a switch where it shows up on the other computers (windows & mac) but not on Ubuntu computer. This computer used to have windows and it showed up there.

---

### Post by red_Marvin on 2006-12-09
switch? Is it a nas (network accessed) storage?

---

### Post by Klarsin on 2006-12-09
These computers are cabled directly to a belkin manual a-b-c-d switch. The Maxtor HD is a direct local connection to each individual computer, and not via a network. It has never needed a driver or software, it is USB 2.0 cabled. I use one just like it for the printer which works just fine with dapper.

---

### Post by red_Marvin on 2006-12-10
An usb switch then. what happens if you connect it directly to the ubuntu computer?
If it works, then it's a problem with the switch.
If it doesn't it might be the file system. (What filesystem do you have on the drive? NTFS?)

---

### Post by christhemonkey on 2006-12-10
If you plug it in, you could give us the output of this command:
```
dmesg | tail 
```

---

### Post by Klarsin on 2006-12-10
OK, it mounts and opens. I should embarass the guy who did the cabling, but I think he is already!

By the way, my Ubuntu computer is FS ext3. What does the following mean about FAT: utf8 is not recommended. 

me# dmesg|tail
[17179607.308000] hda-intel: Invalid position buffer, using LPIB read method ins tead.
[17179615.340000] NET: Registered protocol family 10
[17179615.340000] lo: Disabled Privacy Extensions
[17179615.340000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179615.340000] IPv6 over IPv4 tunneling driver
[17179618.316000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!
[17179673.984000] CSLIP: code copyright 1989 Regents of the University of Califo rnia
[17179673.992000] PPP generic driver version 2.4.2
[17179706.636000] PPP BSD Compression module registered
[17179706.676000] PPP Deflate Compression module registered

Working from different file systems - will this affect editing of files back and fourth between the drives?

---

