---
title: "DVD-Ram stalls system on write"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by lmandrake on 2006-08-14
Hello,

I have a LG GSA-4040B drive with DVD-RAM write capability which works out of the box with my Dapper installation (kernel 2.6.17ck1 and default kernel). Sadly the write process stalls the system every few seconds; I think this is happening when the drive is verifying the written data (which is done by the drive itself). Does anybody know if there are some special paramaters or kernel setups I have to set to prevent the stall? I really love this verification but this is no reason I can't even surf the web anymore while copying at 1.5mb/sec.

I'm using udf filesystem and udma2 is enabled (just checked with hdparm).

Thanks in advance for your suggestions

---

### Post by John.Michael.Kane on 2006-08-16
lmandrake you say it works with both kernel's,however. you don't state which kernel causes the stalling.

---

### Post by lmandrake on 2006-08-16
I can read and write DVD-RAM with both kernels and the stalling appears under both. I just setup udftools properly and now it's slightly better; meaning a little bit faster but still there are these annoying stalls where my mouse or the programs I use hang.

---

### Post by John.Michael.Kane on 2006-08-16
lmandrake the burner might not be causing this. are any other sevices are running?

What are your system spec's?

---

