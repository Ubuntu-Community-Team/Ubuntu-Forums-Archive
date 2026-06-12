---
title: "Scanner support for Raven Original"
date: 2020-09-26
forum: Hardware
---

### Post by yaminb on 2020-09-26
Anyone know if it's possible to get the Raven Original Scanner working under twain in Ubuntu (20.04).
I've checked here: [http://www.sane-project.org/sane-backends.html#SCANNERS](http://www.sane-project.org/sane-backends.html#SCANNERS) 
I can't find it, maybe it's possible.

[https://www.raven.com/products/raven-scanner-original](https://www.raven.com/products/raven-scanner-original)

Thanks,

---

### Post by kurt18947 on 2020-09-26
I suspect this will be a real challenge if it's possible at all. I'd maybe try wine or play on Linux without any real hope. That isn't just a scanner by the looks of it but an entire document management system that probably uses lots of Windows services. I use Gscan2pdf as a scanner front end but that's using a scanner (Brother MFD) that is well supported by Ubuntu.

---

### Post by CelticWarrior on 2020-09-26
[https://www.raven.com/pages/raven-scanner](https://www.raven.com/pages/raven-scanner)

This shows USB connectivity as "Flash Drive and Computer TWAIN" for the PRO but "Flash Drive Only" for Original. So, yours has network and local USB media only, it isn't intended for USB connection with a computer.

---

### Post by yaminb on 2020-09-28
Thanks.

So how would one use a scanner over wifi? Pardon my ignorance... I thought over wifi, we'd still need 'wifi twain' driver.
Probably bad terminology. What is the wifi scanning driver called? From a quick google WIA?

---

### Post by CelticWarrior on 2020-09-28
Again, the Original is NOT intended to be used connected to a computer either by cable or network. It either uses files from and saves files to USB media -or- their cloud, that's it. 
OTOH, the Pro model can be used with a USB cable like any typical scanner, supposedly but not necessarily via network, and the same Cloud service also available for the Original one.
That's all there is to know about those devices. This can be easily understood just by reading the user's manual. Please do as your question has nothing to do with Ubuntu. The way to use your scanner must always be via the Cloud or some USB stick, either way regardless of the OS as you only need a web browser to locally download the files.

---

