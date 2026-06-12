---
title: "Trying to mount bsd filesystems from HDD using live Dapper"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by Seti on 2006-06-05
The grfx card and/or my motherboard in my main desktop got toasted so now I'm temporarily using my 2nd computer as a desktop. It's normally a little server I have run by openbsd. So the thing is normally for ftp and httpd, but now I'm running a live Dapper CD on it because of the Tragedy.
Now I'd like to be able mount these partitions....
$ dmesg | more gives:

[   58.126767] ide1 at 0x170-0x177,0x376 on irq 15
[   58.293120] hda: max request size: 128KiB
[   58.831711] hda: 20015856 sectors (10248 MB) w/512KiB Cache, CHS=19857/16/63, UDMA(33)
[   58.831797] hda: cache flushes not supported
[   58.833577]  hda: hda4
[   58.845244]  hda4: <openbsd: hda5 hda6 hda7 hda8 hda9 >
[   58.853929] hdb: max request size: 128KiB
[   58.870237] hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, (U)DMA
[   58.871894] hdb: cache flushes supported
[   58.873465]  hdb: hdb4
[   58.883154]  hdb4: <openbsd: >

I searched around but couldn't seem to find anthing. Is there some kind of support for this??

---

### Post by mips on 2006-06-05
Eh, as far as I know *BSD use different filesystems to linux but you should at least be able to read them I 'think'.

The only suggestion I have is google. Hopefully someone else here has better advise.

---

### Post by soapyfish on 2008-01-21
I searched for many hours without any sucess in the end I just installed OpenBSD on another system and mounted the disk locally and moved the files over shh.  

I did see some posts suggesting that the command below would do it but I had no joy.   

mount -r -t ufs ufstype=old  /dev/diskname /mountpoint/folder/

other posts suggested that 

mount -r -t ufs ufstype=bsd44  /dev/diskname /mountpoint/folder/

or

mount -r -t ufs bsd44  /dev/diskname /mountpoint/folder/

If that helps anyone please post a response

---

