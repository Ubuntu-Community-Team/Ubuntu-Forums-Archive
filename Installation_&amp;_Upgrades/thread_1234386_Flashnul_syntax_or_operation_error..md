---
title: "Flashnul syntax or operation error."
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by pofadda on 2009-08-07
Following thread:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
reference is made to getting the 'physical drive' via flashnul -p

This shows drive letters, not the number that seems to be needed.  Running flashnul I: -L ubuntu...img says 'file is being used by another process'.  Which is odd as it appears even though the drive has only just been inserted and is not being interacted wit, not even by Explorer.

I tried substituting '9' for 'I:' (9th letter) but that didn't help.

What have I done wrong???

---

### Post by HackerBaloo on 2011-12-14
Well, I had the same problem, but found the solution. Use the drive letter and:
Numbers are for physical drives and letters are used for logical drives.
I got this
d:\>flashnul.exe -p

Avaible physical drives:

Avaible logical disks:
C:\
D:\
E:\
F:\
G:\
H:\
Y:\
Z:\


Press ENTER to exit.

So then I could run:

d:\>flashnul.exe H: -L g:\ChromeOS-Vanilla-1424.0.2011_12_14_1628-rb3d36ad0.img

---

