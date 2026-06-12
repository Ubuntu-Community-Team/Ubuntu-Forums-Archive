---
title: "Epson Stylus CX5400 problem"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by lewisdw on 2005-06-21
I have an epson stylux CX5400 (combo printer, scanner) that was detected via SANE under ubuntu live dvd with no problems, right from the start.  Now that I have installed ubuntu to my hd, SANE will no longer detect the cx5400.  How do I resolve this so I can scan?

---

### Post by lewisdw on 2005-06-27
Anyone?  Please!

---

### Post by gc1 on 2005-07-01
You are not alone. I can't get my CX3600 to come to life. Many Epson printers listed but not these all in one types. Please help us

---

### Post by David Haas on 2005-07-03
I'd go to the Epson support Web site for the CX5400: <http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&oid=25301&infoType=Overview>

I didn't see a listing for the CX3600, but there is one for the CX3200: <http://www.epson.com/cgi-bin/Store/support/supDetail.jsp?BV_UseBVCookie=yes&oid=14082&infoType=Overview>

I hope this helps.

David

---

### Post by gc1 on 2005-07-04
Thanks Dave, I had already visited Epson for that CX3200 help but could not carry out what was suggested because when I connected to [http://localhost:631](http://localhost:631) and selected Manage Printers I was asked for a password which I didn't know.
New problem now: I can't get localhost:631, I get the message "connection refused". Perhaps I have spoilt my access by doing something wrong? Where is localhost:631?  Inside my OS?

---

### Post by David Haas on 2005-07-09
gc1--I gather that you've contacted Epson and received some information on obtaining and installing the driver (PPD file) for your printer. I don't know enough to understand what instructions you received, and I don't know enough to see how it would relate to localhost;631. You should be able to communicate via email with Epson on this. Another option is to describe their instructions to you and your problem with them and begin a new thread on this.
David

---

### Post by Strangerdave on 2005-07-16
Humm, I too am having a problem with my CX5400 being noticed.  I think the printer installed okay, but don't know how to scan.

I just installed Ubuntu and am extremely ignorant - please bear with me while I learn

SD

---

### Post by HellHoundsofwar on 2007-09-20
hi eveyone 
this has worked for me even after restarting the computer a few times

-open terminal  copy and paste the following-

sudo sane-find-scanner | grep 0x04b8
found USB scanner (vendor=04b8,
product=0x0808) at libusb:001:002

then go to xsane image scanner your scanner should now be detected

---

