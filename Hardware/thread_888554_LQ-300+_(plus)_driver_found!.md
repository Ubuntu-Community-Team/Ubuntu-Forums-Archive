---
title: "LQ-300+ (plus) driver found!"
date: 2008-08-13
forum: Hardware
---

### Post by kstan_79 on 2008-08-13
for those having problem with lq-300+, can see info here. I struggling it quit sometimes.
[http://www.extraknowledge.org/forum/viewtopic.php?p=1069#1069](http://www.extraknowledge.org/forum/viewtopic.php?p=1069#1069)
I happy with the result. Please spread this info out.

---

### Post by seetho on 2008-10-13
Doesn't work for me.  All it does is just prints pages upon pages of garbage until it runs out of paper.

Anyone else having better luck at getting this printer to work?

---

### Post by kstan_79 on 2009-01-08
Can I know how you install this driver? It work fine at all machine I have.
I have Ubuntu 8.04 x 2, 8.10 x 1. All work like usual.

By the way, what papersize you use?

---

### Post by kstan_79 on 2009-01-08
Can I know how you install this driver? It work fine at all machine I have.
I have Ubuntu 8.04 x 2, 8.10 x 1. All work like usual.

By the way, what papersize you use?

---

### Post by seetho on 2009-05-15
It is working now on 9.04.  It turns out the problem was in the USB to parallel port thing that I had.  I used another one and now it works.

---

### Post by seetho on 2009-06-10
More comprehensive information to those who are looking to use the Epson LQ-300+ with Ubuntu.

You can download the ppd from [http://www.cups.org/ppd/epson/en/eplq300.ppd.gz](http://www.cups.org/ppd/epson/en/eplq300.ppd.gz)

I just copied the .gz (don't extract the ppd) file to /usr/share/foomatic/db/source/PPD/Epson/
(not sure where else I can put it).

Goto System->Administration->Printing and add a new printer.  I have connected the printer with one of those cheap USB to Parallel cables.  The printer is detected as EPSON LQ-300+

Select driver under Epson and you should see it listed as LQ-300+ 24 pin.

CAUTION!: The max resolution you can use under "Printer Options" is 360x180dpi.  DO NOT select the highest 360dpi setting - your printer will go crazy and eat-up all your paper.

It works for me.  I hope it works for you too.

---

### Post by tdapower on 2011-02-10
Your driver is fine, But I have a problem when printing on continuous papers, That is when printing on continuous papers, first page printed finely and after that another paper automatically feeded and stopped. So how do I overcome this?

---

### Post by seetho on 2011-02-25
> **tdapower said:**
> Your driver is fine, But I have a problem when printing on continuous papers, That is when printing on continuous papers, first page printed finely and after that another paper automatically feeded and stopped. So how do I overcome this?

I had paper feeding problems when I upgraded my OS a while ago.  Now I find the "Epson 24-Pin Series" driver to be working well.  Remember use US-Letter paper size and set resolution to no higher than 360x180.

---

### Post by tanapon on 2011-07-28
Try this one;

[http://www.cups.org/ppd/epson/en/eplq300.ppd.gz](http://www.cups.org/ppd/epson/en/eplq300.ppd.gz)

---

### Post by Jack Brown on 2011-10-13
Hi did you guys get alternating blank pages with text pages that printed properly?  (for multiple page documents)

if yes,  were you able to fix it?, How?






____
Hold on..  things are looking up :)

---

