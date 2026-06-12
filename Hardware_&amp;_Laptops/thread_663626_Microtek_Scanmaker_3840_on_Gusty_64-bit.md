---
title: "Microtek Scanmaker 3840 on Gusty 64-bit"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Malinthe on 2008-01-10
Hi Guys,

I moved from Windows to Ubuntu few days ago. I've tried Ubuntu 7.04 and I have installed Ubuntu 7.10 64-bit version on my 64-bit AMD machine. Currently, I am unable to get my scanner to work with Gutsy. It worked fine with the previous version of ubuntu and I've searched many forums and didn't find a solution.

The scanner is a Microtek Scanmaker 3840. When I load xsane it detects the scanner. After I select it I get this error message:

Failed to open device 'sm3840:libusb:002:004': Access to resource has been denied.

I tried many things but they didn't work. Including running xsane as root. None of them worked. Glad if anyone can fix this problem. I'm new to Linux and I hope to stick with it for a long time. Please help guys :)

---

### Post by Malinthe on 2008-01-11
Oh guys pls help me!
I tried the Feisty Live CD and the scanner worked fine with it.
So why doesn't gutsy work with my scanner?

---

### Post by onfyreforjesus on 2008-01-17
same problem with 32 bit gutsy! it worked well with feisty..

even on sudo xsane in the terminal i get the same problem.:(

---

### Post by artlion on 2008-02-08
[http://www.ziplabel.com/sm3840/](http://www.ziplabel.com/sm3840/)

Problem is not with scanner, but with sane (xsane) newer than 0.15

ArtLion

---

### Post by alienexplorers on 2008-05-17
The sane 1.0.19 driver is bad as far as I know.  I reverted back to the 1.0.15 driver and now everything works fine.

---

