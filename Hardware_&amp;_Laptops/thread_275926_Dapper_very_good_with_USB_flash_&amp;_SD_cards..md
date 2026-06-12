---
title: "Dapper very good with USB flash &amp; SD cards."
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by harry555 on 2006-10-12
I've had very good results using 256 mb USB flash drive.  It works perfectly with the built in USB 1.1 ports and also on USB 2.0 add in PCI card. 

I am also using a MFC215c MFU which I got going using the howto listed elsewhere.(Prints and scans just fine)   On this MFC215C there is a slot for SD memory cards and it works perfectly.  

In the last few days I have tried some other distros to check out how well they deal with USB flash cards.   Dapper trounces them!   Mandrake 10.1 would not work at all.   SUSE 10.0 was quite good but got 'confused' between the flash stick, and the SD card.   Xandros Open edition 3.02 was very good too at handling the USB flash.   But the free version of Xandros has too many limitations for me.

---

### Post by fedupwithwin on 2006-10-12
I have had nothing but trouble trying to get my USB memory stick to work on my USB 1.1 ports.  I believe Ubuntu is having problems with my USB 1.1 host controller (I believe it's made by VIX?). Could you please tell me what type/brand/part number of USB host controller you have in your system?  You can access this with "lspci -v" from the terminal.

Thanks In Advance,

---

### Post by fedupwithwin on 2006-10-12
Whoops!  The USB Host controller is made by VIA not VIX.  I also noticed in my log file that Ubuntu may not like "FAT: utf8" file systems.  Hmmmmmm.

---

### Post by dannyboy79 on 2006-10-12
> **fedupwithwin said:**
> Whoops!  The USB Host controller is made by VIA not VIX.  I also noticed in my log file that Ubuntu may not like "FAT: utf8" file systems.  Hmmmmmm.

it's not saying that it doesn't like it, it is merely pointing out that FAT: utf8 is not a recommended IO charset for FAT filesystems and that the filesystem will be Case Sensitive. which when you think about it doesn't make sense because XP formats fat32 as utf8 as the IO charset. It is ok to see this, i read that a bug has been reported and that hopefully it'll be fixed in a kernel update or at least with Edgy.

---

### Post by fedupwithwin on 2006-10-12
Cool...  Thanks - one less thing to investigate.  Now, about that USB host controller...  Hmmmmmm...

---

