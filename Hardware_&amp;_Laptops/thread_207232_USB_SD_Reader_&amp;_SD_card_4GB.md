---
title: "USB SD Reader &amp; SD card 4GB"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by Typhoe on 2006-07-01
Hi,

I try to read/write on a SD card of 4GB using a Usb SD Card Reader and can't get it to work...

To be precise:
- Card reader + SD 2GB = working
- Card reader + SD 4GB = not working
- Card Reader + SD 4GB + OS WindowsXP = working (so it should be possible under linux and the SD 4GB is not broken)

As an attachment, I join the output of the dmesg command.

If someone can help me... Thanks!

Regards,
Typhoe

---

### Post by Typhoe on 2006-07-04
up.

Nobody has encounter the same problem or have any idea what I could do?

Thank you.

Typhoe

---

### Post by dogeatery on 2006-07-11
i'm having a similar problem with my USB SD/MMC card reader.  in the first place nothing wants to automount on my computer.  this means doing it manually but I have no idea what to mount it as.  I usually use sda1 for a USB memory stick but this card reader is confusing me.  anyone have any advice for either of us?

---

### Post by Typhoe on 2006-07-11
Hi,

my card seems to be the problem.

Although it is detected by my PDA or WindowsXP (for example) as a 4GB Sd, neither of them can write more than 1GB of data on it. If I try, the card becomes unusable (can't read/write on it anymore).

In the dmesg log, there is these lines:
sd 6:0:0:0: Device not ready.
end_request: I/O error, dev sda, sector 7926903

So I think that the card is detected as defectuous and so, not mounted...

Regards,
Typhoe

---

