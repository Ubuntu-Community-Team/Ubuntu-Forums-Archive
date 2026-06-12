---
title: "Boot Error"
date: 2010-03-01
forum: Hardware
---

### Post by livecdobsessed on 2010-03-01
My install of Ubuntu 9.10 is not booting any more; when searched, it gives the message of
[8.114979] ata1.00: status: {DRDY ERR}
[8.114981] ata1.00: error: {ABRT}
[8.115466] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[8.116070] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[8.116073] ata1.00: configured for UDMA/100
[8.115079] sd 0:0:0:0: [sda] Result: hostbte=DID_OK driverbyte=DRIVER_SENSE
[8.116082] sd 0:0:0:0: [sda] Sense Key: Aborted Command [current] [descriptor]
[8.116086] Descriptor sense data with sense descriptors
[8.114981] 72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00
[8.116099] 17 49 f1 a8
[8.116103] sd 0:0:0:0: [sda] Add. Sense: No additional sense information
[8.116107] end_request: I/O error, dev sda, sector 390721960
[8.116115] ata1: EH complete
Meanwhile, my Release Candidate version of Windows 7 expires today, meaning that if this doesn't get fixed I'll be left with a useless brick of plastic and... whatever else they use to make laptops.

---

### Post by six30two on 2010-03-01
Unix based OSes are never useless ;)

You could try popping in a Live CD and running the recovery console, if you can't access it normally.

---

### Post by livecdobsessed on 2010-03-01
> **six30two said:**
> Unix based OSes are never useless ;)

You could try popping in a Live CD and running the recovery console, if you can't access it normally.

I mean, my linux isn't booting properly at all, and I *am* using a live cd to fix it if possible.

---

### Post by livecdobsessed on 2010-03-02
The Live CD can't write to my hard drive, nor can it access it, but it can tell how much total space it has, and that's about it for what it could do.

---

### Post by psusi on 2010-03-02
What do the following commands have to say?

sudo hdparm -I /dev/sda
sudo fdisk -l /dev/sda

---

### Post by www.rzr.online.fr on 2010-09-24
hi

I fear I have a broken hdd :


[http://rzr.online.fr/q/ata](http://rzr.online.fr/q/ata) : how to #recover a #harddisk #failure "end_request: I/O error, dev sda, sector 0" : scaring !linux #dmesg #log ?


Can you explain those lines :

sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sda:
sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sd 0:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]


Regards

---

