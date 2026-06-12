---
title: "Slow USB transfer"
date: 2009-11-28
forum: Hardware
---

### Post by PatrickVogeli on 2009-11-28
Hi there,

I know this has been widely discused here, but are you people having better luck with Karmic??

I suffer from this now too. USB slows down to 2-4MB/s.. Yesterday I want to burn a DVD using my USB burner and 3 discs failed, I had to boo into windows to burn the DVD. 

After doing more tests, I realize it's surely a slow USB related problem.

How's it going for you? Any fix? BTW, I'm using a 2.6.31.6 kernel.

---

### Post by BALJEET OBEROI on 2009-11-28
i am also observing the same problem basically it is i think due to non compatibility of usb device for ubuntu 
usb devices are compatile with windows & mac 
i got this information from Manufacturer of my usb device

---

### Post by PatrickVogeli on 2009-11-28
I have tried the pci=routeirq, elevator=as, deadline or noop with success.

I had no succes: transfer to usb stick is always painfully slow. It starts fine, but after ~260MB it slows down. Makes it completely unusable...

On the other side, I have a 120GB Western Digital USB hard drive (2,5") and transferring to that one works fine. It is ext3 formated.

---

