---
title: "How to read burnt DVD disc from Vista computer"
date: 2008-08-01
forum: Hardware
---

### Post by F8M on 2008-08-01
My Laptop Ubuntu 8.04 LTS can't read the PDF files from the burnt Data DVD off my Vista laptop but it can from my 3rd computer(XPpro) that burnt the same files. 
How can I resolve my problem of reading the PDF burnt files from my Vista computer? Do I need to change the way the burnt DVD is formatted so it can be read on my Ubuntu?

---

### Post by stchman on 2008-08-01
> **F8M said:**
> My Laptop Ubuntu 8.04 LTS can't read the PDF files from the burnt Data DVD off my Vista laptop but it can from my 3rd computer(XPpro) that burnt the same files. 
How can I resolve my problem of reading the PDF burnt files from my Vista computer? Do I need to change the way the burnt DVD is formatted so it can be read on my Ubuntu?

I had this problem before, you need to burn the disc on Windows using ISO9660 with a secondary volume descriptor of Joliet.

Do not use the built in DVD burner of Vista or XP use Infrarecorder as it is the best free DVD/CD burner for Windows.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

You will need to reburn your discs using the standard I mentioned above.

---

### Post by mc4man on 2008-08-01
If you use the mastered mode in vista your data dvd should be fine (vs. the default 'live file system'). For data dvds using iso9660, udf extensions (udf 1.02) is what you want, though adding Joliet doesn't hurt. 
Data cds should have iso9660,Joliet ext.'s.

---

