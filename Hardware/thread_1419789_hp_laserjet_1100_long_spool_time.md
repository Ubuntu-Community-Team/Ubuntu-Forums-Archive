---
title: "hp laserjet 1100 long spool time"
date: 2010-03-02
forum: Hardware
---

### Post by chudecapo on 2010-03-02
I have a printserver with ubuntu and when i send a print job from an Ubuntu terminal, the printer responds too slowly (about 1 min) and then starts printing. When the job is sent from a Windows terminal, it starts inmediately. How can i speed up the spooling when i print from a ubuntu terminal?

---

### Post by Barcobus on 2011-08-12
I too have this problem although the printer did not do this initially. My pages print one at a time with 1min spool also even if I print 50 identical pages. #-o What did you change since your install of Ubuntu?

---

### Post by Barcobus on 2011-08-12
Try to manually replace all the dependencies and update your install.

[Manual Install instructions]("http://sourceforge.net/projects/hplip/files/hplip/3.11.7/hplip-3.11.7.tar.gz/download")

Following these instructions I replaced my printer install. Pages printing 1 per second now :popcorn:

---

### Post by Fatty_Matty on 2011-09-02
Hello,

I'm fairly new to Ubuntu/Linux so please be patient! I've tried installing my HPLJ1100 printer with HPLip however the setup doesn't recognise it. Ubuntu does recognise the printer through Admin/Sys/Printer and prints albeit with a long spool time.

I suppose my question is, how do i manually replace the dependenies and what ones should i replace to ensure a fast spooling time?

Thanks!

---

### Post by foresthill on 2011-09-02
> **Barcobus said:**
> Try to manually replace all the dependencies and update your install.

[Manual Install instructions]("http://sourceforge.net/projects/hplip/files/hplip/3.11.7/hplip-3.11.7.tar.gz/download")

Following these instructions I replaced my printer install. Pages printing 1 per second now :popcorn:

There aren't any instructions that I saw. 

Which distro are you using? I have had slow printing problems on my HP 1320 Laserjet going back to at least version 9.10, especially with PDF files. 

The solution for me was always to install either XPDF or Okular, but these programs don't work in 11.04. So if I want decent printing time for PDF files, I have to stay with 10.10. 

If I could find a way to get PDF's to print normally, I'd love to be able to use 11.04.

---

