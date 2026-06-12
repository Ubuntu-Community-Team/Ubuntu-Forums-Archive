---
title: "problem mounting memory stick"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by alin4lex on 2006-12-28
```
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab
Please check that the device is plugged correctly.
```

this is the error that DAPPER reports when i plug in a memory stick or memory card(MMC)

---

### Post by djgrandmarquis on 2006-12-28
I recommend upgrading to Edgy. Peripheral connectivity is greatly improved in Edgy and your card will most likely pop up as /media/<devicename>. My USB hard drive is easier to connect than ever before, no need to mess with mtab or fstab.

In the meantime, this tutorial helped me in Breezy/Dapper.
[http://www.novell.com/coolsolutions/feature/11637.html#first](http://www.novell.com/coolsolutions/feature/11637.html#first)

---

### Post by TheWizzard on 2006-12-28
> **djgrandmarquis said:**
> I recommend upgrading to Edgy. Peripheral connectivity is greatly improved in Edgy and your card will most likely pop up as /media/<devicename>. My USB hard drive is easier to connect than ever before, no need to mess with mtab or fstab.

In the meantime, this tutorial helped me in Breezy/Dapper.
[http://www.novell.com/coolsolutions/feature/11637.html#first](http://www.novell.com/coolsolutions/feature/11637.html#first)

i'd only upgrade to edgy if you don't use your computer for work, etc. dapper is long term support and intended to be more stable. 
if you want to upgrade to edgy, make sure you do a clean install! 

dapper should recognise your usb drive and put an icon on the desktop
you can take a look at the error messages with this command:
```
tail -f /var/log/syslog
```
the output will tell you what goes wrong when you plug in your usb drive.

---

### Post by Footer on 2006-12-29
I upgraded to Edgy recently and am having trouble reading my memory sticks, memory cards, etc.  I get the pop-up window asking me what I want to do (Open in New Window/Do Nothing) but when I click OK (Open in New Window), nothing happens.

Here's the output from /var/log/syslog:

Dec 29 11:10:15 kubuntu kernel: [17758673.348000] SCSI device sdb: 2031120 512-byte hdwr sectors (1040 MB)
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: Write Protect is off
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: Mode Sense: 03 00 00 00
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: assuming drive cache: write through
Dec 29 11:10:15 kubuntu kernel: [17758673.364000]  sdb: sdb1

Any ideas?

Thanks.

---

### Post by TheWizzard on 2006-12-29
> **Footer said:**
> I upgraded to Edgy recently and am having trouble reading my memory sticks, memory cards, etc.  I get the pop-up window asking me what I want to do (Open in New Window/Do Nothing) but when I click OK (Open in New Window), nothing happens.

Here's the output from /var/log/syslog:

Dec 29 11:10:15 kubuntu kernel: [17758673.348000] SCSI device sdb: 2031120 512-byte hdwr sectors (1040 MB)
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: Write Protect is off
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: Mode Sense: 03 00 00 00
Dec 29 11:10:15 kubuntu kernel: [17758673.364000] sdb: assuming drive cache: write through
Dec 29 11:10:15 kubuntu kernel: [17758673.364000]  sdb: sdb1

Any ideas?

Thanks.

what if you try: 
```
sudo mount /dev/sdb1 /media/sdb1
```

---

### Post by Footer on 2006-12-29
Well, that would probably work ... But on a whim, I decided to reboot (I've been running for almost a week without a reboot) and now everything magically started working.  Here's the output of /var/log/syslog:

Dec 29 17:45:33 kubuntu kernel: [17180354.080000] SCSI device sdb: 2031120 512-byte hdwr sectors (1040 MB)
Dec 29 17:45:33 kubuntu kernel: [17180354.092000] sdb: Write Protect is off
Dec 29 17:45:33 kubuntu kernel: [17180354.092000] sdb: Mode Sense: 03 00 00 00
Dec 29 17:45:33 kubuntu kernel: [17180354.092000] sdb: assuming drive cache: write through
Dec 29 17:45:33 kubuntu kernel: [17180354.112000] SCSI device sdb: 2031120 512-byte hdwr sectors (1040 MB)
Dec 29 17:45:33 kubuntu kernel: [17180354.128000] sdb: Write Protect is off
Dec 29 17:45:33 kubuntu kernel: [17180354.128000] sdb: Mode Sense: 03 00 00 00
Dec 29 17:45:33 kubuntu kernel: [17180354.128000] sdb: assuming drive cache: write through
Dec 29 17:45:33 kubuntu kernel: [17180354.128000]  sdb: sdb1
Dec 29 17:45:37 kubuntu kernel: [17180358.424000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

It mounts very quickly, and Konqueror comes up automagically showing the memory card as it did under Dapper.

Weird but I'm a happy camper again!

Thanks for the reply!

:)

---

### Post by TheWizzard on 2006-12-29
> **Footer said:**
> Well, that would probably work ... But on a whim, I decided to reboot (I've been running for almost a week without a reboot) and now everything magically started working.  Here's the output of /var/log/syslog:


i think this is a kde issue. this happens to me now and then. 
i'm not sure what causes this. 
log out and back into kde should be sufficient.

---

