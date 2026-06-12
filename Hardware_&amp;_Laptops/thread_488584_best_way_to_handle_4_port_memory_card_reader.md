---
title: "best way to handle 4 port memory card reader?"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by gnychis on 2007-06-30
Hey all,

I was wondering what the best way to handle a 4 port memory card reader is to get stable mount points.  It's an 8 in 1 Sandisk card reader which has 4 ports.  When i plug it in I see:

```

[62564.620609] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
[62564.621983] scsi 8:0:0:1: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
[62564.623228] scsi 8:0:0:2: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
[62564.624592] scsi 8:0:0:3: Direct-Access     Generic  STORAGE DEVICE   0001 PQ: 0 ANSI: 0
[62564.626264] sd 8:0:0:0: Attached scsi removable disk sdf
[62564.626325] sd 8:0:0:0: Attached scsi generic sg6 type 0
[62564.628580] sd 8:0:0:1: Attached scsi removable disk sdg
[62564.628647] sd

 8:0:0:1: Attached scsi generic sg7 type 0
[62564.629950] sd 8:0:0:2: Attached scsi removable disk sdh
[62564.630014] sd 8:0:0:2: Attached scsi generic sg8 type 0
[62564.631278] sd 8:0:0:3: Attached scsi removable disk sdi
[62564.631342] sd 8:0:0:3: Attached scsi generic sg9 type 0

```

When I plugin a card to one of the slots I see:
```

[62605.028641] SCSI device sdi: 1963008 512-byte hdwr sectors (1005 MB)
[62605.029893] sdi: Write Protect is off
[62605.029897] sdi: Mode Sense: 02 00 00 00
[62605.029900] sdi: assuming drive cache: write through
[62605.032018] SCSI device sdi: 1963008 512-byte hdwr sectors (1005 MB)
[62605.033521] sdi: Write Protect is off
[62605.033527] sdi: Mode Sense: 02 00 00 00
[62605.033531] sdi: assuming drive cache: write through
[62605.033906]  sdi: sdi1

```

Whats the best way to handle this?  I'm not sure I want to assign UUIDs to specify mount points in fstab, because I want *any* SD card to map to the same point and so on.  I also don't think /dev/sdi is stable, know what I mean?  Like I could reboot or add another device and it could be come sdj ...

I'd greatly appreciate any suggestions.

Thanks!
George

---

### Post by jdawiz on 2007-07-17
Has no one answered this or is there another thread on this.  I would like to know also.  I have converted my 85 year old grandfather to kubuntu.  He lives in Illinois and I live in Georgia.  When he brought his laptop down for me to install he didn't bring the card reader.  So now that it is at his house it doesn't pop up with the "what do you want to do" screen that I was expecting.  I can ssh into his machine from here but I need to know if anyone can help me figure out why it wouldn't "pop up".  My external usb drive did when I plugged it into this same computer.  Thanks for any help you can give.  

Jeremy

---

