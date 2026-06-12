---
title: "Philips DVD burner not reading CD?"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by mathijs on 2005-11-20
I'm having troubles installing ubuntu (5.10) when I use a philips DVD burner. Somewhere in the process of installing, the installer says the CD is corrupt. However, on any other cd player I try the CD, it works. The md5 checker even returns no error on the exact same CD in the philips player on windows! So it must be some linux issue.

The cd burner is recognized as "hdc: PHILIPS DVDR1628P1, ATAPI CD/DVD-ROM drive" (which is weird, because it actually is a DVD burner), and during install, messages like "hdc: error on read" start popping up, leading to the message that the CD is corrupt. Is this some driver issue that will be resolved in the future?

---

### Post by juicybananahead on 2005-11-20
Have you tried the media check that's available at the bottom of the installation menu?

---

### Post by mathijs on 2005-11-21
Yes, of course. The point is that when booting from the CDROM, the check says the CD is invalid, but when I boot in windows, the CD just reads fine (all md5sums are correct).

---

### Post by mathijs on 2005-11-28
I have found the problem: dma was not supported for my motherboard, and once I did enable it, the read errors were gone.

---

