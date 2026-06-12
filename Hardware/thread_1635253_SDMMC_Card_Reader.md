---
title: "SD/MMC Card Reader"
date: 2010-12-01
forum: Hardware
---

### Post by Sailor5 on 2010-12-01
Urg not you again.

Disappointments aside. I just got a SD/MMC card reader. Which doesn't seem to want to work. I've tried three different SD cards to no avail. So it must be the device itself. It also interfers with the computer. If it's plugged in on boot up. It will hang on the BIOS screen and will not continue until removed.

[http://pastebin.com/eCrBjupv](http://pastebin.com/eCrBjupv) dmesg output

Never get electronics from the pound shop.

Thanks Bye!

---

### Post by dandnsmith on 2010-12-01
I'd guess, from that log file, that you have a card plugged into the reader, and that is what is causing the problem (you can see all the block errors).

I've seen a similar log with a (known) faulty CD device with a CD in it at boot.

A further problem might be the current draw - perhaps the device draws too much along with the draw from other devices at boot - this has been known to happen with too many of the wrong sort of usb device at boot (usb hubs which are not independently powered, usb adsl modems ...)

---

### Post by Sailor5 on 2010-12-01
> **dandnsmith said:**
> I'd guess, from that log file, that you have a card plugged into the reader, and that is what is causing the problem (you can see all the block errors).

I've seen a similar log with a (known) faulty CD device with a CD in it at boot.

A further problem might be the current draw - perhaps the device draws too much along with the draw from other devices at boot - this has been known to happen with too many of the wrong sort of usb device at boot (usb hubs which are not independently powered, usb adsl modems ...)

So a different reader is in order? I did have a different one but unfortunately it was lost. However that worked fine. Damn you poundland.

---

### Post by b0b138 on 2010-12-01
I had a problem like that once but it was from my new cards, which are the high capacity cards, didn't work in my old pre-HCSD reader.

---

### Post by dandnsmith on 2010-12-03
Yes, that could be a possibilty, but might be precluded by the choice of the 3 cards - only OP can tell us that

---

