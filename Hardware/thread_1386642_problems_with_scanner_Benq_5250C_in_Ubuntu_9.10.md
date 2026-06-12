---
title: "problems with scanner Benq 5250C in Ubuntu 9.10"
date: 2010-01-20
forum: Hardware
---

### Post by kaustikos on 2010-01-20
Hello everybody!
 
I have a problem employing Benq scanner 5250 C in Ubuntu 9.10. I use it on a Lenovo Thinkpad SL500 laptop. As far as I understand, to use a scanner in Ubuntu one has to attach a *.bin file from windows driver of the scanner to the SANE program set. I've performed the following steps:
1) installed all sane-related packages in Synaptic
2) downloaded the latest drivers from [http://benq.ru/support/downloads/downloads.cfm/dtype/D/page/downloads/product/558](http://benq.ru/support/downloads/downloads.cfm/dtype/D/page/downloads/product/558)
(I took those for WinXP - I don't know if .bin's differ in different versions of Windows)
3) extracted the *.bin file (u55v009.bin) and put it into /etc/sane.d/
4) edited snapscan.conf file with
 
firmware /etc/sane.d/u55v009.bin
/dev/usb/scanner0 bus=001
 
This solved the problem with starting XSane - it no longer fails being unable to find scanner. Command "sane-find-scanner" finds scanner marked as Acer. Everything appears to be ok until I start scanning. Due to unknown problems scanner "cuts" processed sheet: only a frame of approximately 20 x 15 cm is scanned. All remaining part of image is cut. Apparently scanner thinks that it's size is less then it actually is. All other programs employing scanner have the same problem - they see only a part of image. I'll appreciate any help with this problem. Many thanks in advance,
Pavel

---

### Post by kaustikos on 2010-01-24
Dear community members! Is it possible that there are no solution to my problem?? Please give me a hint! Or have I keep an MS Win only to scan documents??

---

### Post by graffiX on 2010-04-20
I have the same problem, wondering if anyone has come across anything.

Thanks

---

