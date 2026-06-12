---
title: "How to instal an HP cdrom"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by fourdigit on 2008-02-07
I have no clue where to start or how to start. I have an HP CD-writer that I want to install on Kubuntu. Any help would be highly appreciated.

---

### Post by kesman on 2008-02-07
So do you need a program for writing cd's, or a whole cd-rw -drive?

---

### Post by fourdigit on 2008-02-07
> **kesman said:**
> So do you need a program for writing cd's, or a whole cd-rw -drive?

A whole cd-rw drive. I have it connected (it´s not a USB cd-rw drive, it´s internal) but I don´t know how to get it connected.

---

### Post by kesman on 2008-02-08
Are you sure it's not already installed in the system? What happens if you put a cd in it?

---

### Post by fourdigit on 2008-02-09
> **kesman said:**
> Are you sure it's not already installed in the system? What happens if you put a cd in it?

Nothing that I can see. Are there any ways to check that I´m not aware of?

---

### Post by Yellow Pasque on 2008-02-09
Try:
```
sudo cdrecord -scanbus
sudo lshw -businfo -C disk
```

---

### Post by fourdigit on 2008-02-10
> **Temüjin said:**
> Try:
```
sudo cdrecord -scanbus
sudo lshw -businfo -C disk
```

Yeah it´s not connected.

```
fourdigit@ubuntudesktop:~$ sudo cdrecord -scanbus
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
scsibus0:
        0,0,0     0) 'ATA     ' 'WDC WD400BB-75JH' '06.0' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
fourdigit@ubuntudesktop:~$ sudo lshw -businfo -C disk
Bus info          Device     Class          Description
=======================================================
scsi@0:0.0.0      /dev/sda   disk           37GB WDC WD400BB-75JH

```

---

### Post by fourdigit on 2008-02-10
Now how do I go about getting my computer to recognize it?

---

### Post by fourdigit on 2008-02-10
Bump.

---

### Post by kesman on 2008-02-11
Maybe you got the cables wrong? Does windows recognize it? Or have you tried the liveCD?

---

### Post by fourdigit on 2008-02-12
I´m pretty sure I have the cables right.

---

### Post by kesman on 2008-02-13
Can you open up the tray in the cd-drive? Does it show up in bios or when you boot, is it listed? Seems like it's not attached to the system at all.

---

