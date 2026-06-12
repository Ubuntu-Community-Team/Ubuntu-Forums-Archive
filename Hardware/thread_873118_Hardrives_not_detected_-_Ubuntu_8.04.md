---
title: "Hardrives not detected - Ubuntu 8.04"
date: 2008-07-28
forum: Hardware
---

### Post by Blanel on 2008-07-28
I have a setup of 
500 gb SATA
160 gb PATA converted to SATA
120 gb PATA converted to SATA

The problem is that the two lower drives will not be detected. They show up in the boot but show alot of errors until they timeout and get deactivated. I suspect it might be the converters that are the problem, but they work fine under windows. The error messages I get say:

ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata2.00: qc timeout (cmd 0x27)
ata2.00: failed to read native max adress (err_mask =0x4)
ata2.00: failed to recover some devices, retrying in 5 secs
ata2.00: qc timeout (cmd 0x27)
ata2.00 failed to IDENTIFY (I/O error, err_mask=0x5
ata2.00:revalidation failed (errno=-5)
ata2.00: Disabled

Almost that atleast. Was writing it down whilst it was booting. Similar or the same for the second disc (ata3)

Can anyone think of anything that might fix this problem. I am quite new to Ubuntu, but am actually running it right now, and posting this message from my laptop where the OS runs close to perfectly.

Thanks

---

### Post by Blanel on 2008-07-29
bump

This is the converter I use:
[http://satadirect.com/sata_converters.html](http://satadirect.com/sata_converters.html)

---

### Post by Blanel on 2008-07-29
Last time I bump.

After this I'll just give up. I've been trying some different solutions (forget which, but IRQpoll doesn't work)... I think I'll just give up after this if I don't get any replies.

---

### Post by evets25 on 2008-07-29
Yeah that IDE-to-SATA device looks really sketchy... I doubt it would have a linux driver, or if it does it would be really buggy since it's just a random device that does something weird made by a no-name company. Using this type of thing is not common, probably because it creates more problems than it's worth, with drivers and whatnot, in addition to the inevitable performance issues it will have with converting SATA to IDE. Because it's not a commonly used device (or even an uncommonly used device - this is the first time I've heard of this type of device), the chances of someone wanting or needing to create and maintain the linux driver for it are slim to none. 

Sorry I don't have better news for you. :(

---

### Post by Blanel on 2008-07-29
Hmm. The strange part is that it isn't requiered to have any drivers according to the creator of the device. It's supposed to run driverless, and so seems the case in windows.

As far as the OS is concerned, it's supposed to run just like any SATA drive. When checking in windows, they seem to be running exactly the same driver as my other SATA drive.

---

### Post by Sef on 2008-07-29
> Last time I bump.

Don't bump unless 24 hours has gone by.  Otherwise you can get an infraction.

---

### Post by Blanel on 2008-07-31
bump

---

