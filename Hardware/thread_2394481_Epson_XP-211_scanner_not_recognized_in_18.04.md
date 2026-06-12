---
title: "Epson XP-211 scanner not recognized in 18.04"
date: 2018-06-16
forum: Hardware
---

### Post by Tacuabe on 2018-06-16
I had been using this printer/scanner since 2016 with 16.04 via USB cable without any issues. 

Two years ago I bought a Dell XPS-13 9350, formatted the SSD and again installed 16.04 with the same Epson printer. No problems.

With the appearance of 18.04 I decided a fresh install was in order and did so. Now the Epson prints via USB cable but the scanner is not recognized by the scanning programs. Tried Simple Scan, Xsane and Image Scan! for Linux. None of them recognize the scanner but Simple Scan additionally reports: "You need to _install driver software_ for your scanner".

Back in 2016 I had started another thread because initially I was not able to make the Epson work, not even printing. Fortunately, Mike Walsh had provided detailed instructions and following them enabled me to solve the problem. I was never able to print via Network, but this does not bother me as I have little use for that and using a cable is OK.

I made sure I followed the instructions mentioned above to the letter. No luck. I also googled and searched this forum for similar cases, again without success.

Using "sudo sane-find-scanner" I get the following report "found USB scanner (vendor=0x04b8, product=0x08ae) at libusb:001:009". It would appear then that the EPSON (0x4b8) scanner is indeed located. 

Will appreciate any help provided to deal with this issue.

Tacuabe

---

