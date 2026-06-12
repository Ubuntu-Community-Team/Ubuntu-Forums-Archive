---
title: "Input/output error - HP LaserJet 5L, Hardy"
date: 2010-04-16
forum: Hardware
---

### Post by lyrix on 2010-04-16
Hello Everyone!

I have serious problem with my printer **HP LaserJet 5L (Hardy Heron 8.04)**. Recently my device have printed all without complications. The problem's benn rising slowly. I thought it was cable - there was no connection with printer. I bought new USB cable (LPT adapter) and now my laptop sees the printer.

After sending task to the printer after switch on there is no reaction and CUPS says:

```
E [16/Apr/2010:16:27:17 +0200] Resume-Printer: Unauthorized 
```After some time the diode lights but my HP LaserJet 5L doesn't want to print even the testpage. CUPS' Log says:     

    ```
E [16/Apr/2010:16:34:47 +0200] [Job 564] Unable to write print data: **Input/output error** 
```On other forums users had the same problems but with the newest Ghostscript. I have the old one and my device have printed recently when old Ghostscript was installed. I don't know what to do.

Help in fixing this will be apprecitated.

Regards

---

### Post by bernard-cpqtech on 2010-05-07
Hi...

I just had a similar problem with my printer.

4:58:57 ubuntu kernel: [ 3333.987045] usblp1: nonzero write bulk status received: -71

Under CUPS at [http://localhost:631/jobs/](http://localhost:631/jobs/) was seeing...
stopped 
*"Unable to write print data: Input/output error"*

The printer would print part of a page and then stop.

I was using Ubuntu 9.04 and 10.04, same problem...

FIX: Connect the printer DIRECTLY to the computer. My USB hub was causing the problem! (D-Link DUB-H7, with USB 2.0 spec)

Hope this helps!

---

### Post by GGsalas on 2010-08-24
> **bernard-cpqtech said:**
> Hi...

FIX: Connect the printer DIRECTLY to the computer. My USB hub was causing the problem! (D-Link DUB-H7, with USB 2.0 spec)

Hope this helps!

I use a short cord and it works! Thanks.

---

