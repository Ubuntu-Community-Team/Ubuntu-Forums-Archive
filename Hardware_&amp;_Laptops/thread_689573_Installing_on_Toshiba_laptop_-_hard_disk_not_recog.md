---
title: "Installing on Toshiba laptop - hard disk not recognized"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by jal_nl on 2008-02-06
I'm trying to install Ubuntu 7.10 on my Toshiba Tecra S3 laptop (using the live CD), but Ubuntu doesn't recognize the harddisk. There's no device in /dev for it. I looked in the syslog, but cannot find anything related to scsi, ata, sata, ide etc. that would give me a clue what's wrong. There's obviously nothing wrong with the hardware, as Windows XP is installed on it, and works fine. When I start gparted, only /dev/scd0 is recognized, when I choose 'refresh devices', it crashes. So, does anyone have any clue what's wrong, and/or how I can solve this?


JAL

P.S. lspci lists the SATA controller, fdisk -l returns without printing a line.

---

### Post by ajgreeny on 2008-02-06
Try ```
sudo fdisk -l
``` which may give some output and help further.

---

### Post by jal_nl on 2008-02-25
> **ajgreeny said:**
> Try ```
sudo fdisk -l
``` which may give some output and help further.

As I stated in my original post, fdisk doesn't return a single line. Anyone else got a take on this? Anyone else ever installed Ubuntu on a Tecra S3?


JAL

---

### Post by jal_nl on 2008-03-01
I just tried a lshw, and that only reports /dev/cdrom, not any hd. Anyone a guess what I can do more?


JAL

---

### Post by jal_nl on 2008-03-02
Some more news: Fedora install has the same problem as Ubuntu. Knoppix however recognizes the hard disk fine, as /dev/sda1.


JAL

---

