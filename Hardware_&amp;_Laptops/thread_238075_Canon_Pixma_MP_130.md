---
title: "Canon Pixma MP 130"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by rjpa on 2006-08-17
Hi,

Does anyone have a clue how to setup a **Canon Pixma MP 130** printer in Ubuntu?

Cheers

rjpa

---

### Post by finite9 on 2006-08-17
sorry to disappoint but there are no driver for Canon PIXMA MP multifunction printers.  There are drivers for Canon PIXMA IP Printers, but these are just printers, not scanners/copiers.  I have a PIXMA MP450 and I have seen on Canons Japanese web site (not easy to understand) that they do have drivers for a Pixma printer (not scanner though), but these are RPMs only for i386 architecture.  As we use Debian based distro we need .DEB files.  I suppose you could try to convert the RPM to DEB using the alien package, and if you also have amd64 version of Ubuntu, you could use dpkg --force-architecture --install <package> but this was too much even for me :(

Basically we are sh*t out of luck.  I bought my PIXMA just weeks before developing a serious interest in GNU/Linux--I really regret buying it now.

---

### Post by rjpa on 2006-08-18
Hi,

Actually got it working using Turboprint 1.94-4. Try that one.

- rjpa

---

### Post by finite9 on 2006-08-19
Jepp, sorry for forgetting to mention that...you can get a driver through Turboprint, but it's not free software.  I actually asked them if they had a driver for the MP450 and 2 weeks later then mailed me saying they had a driver for MP450/MP500.

I'm not willing to buy the software though--would prefer a native driver.  I heard that there is a driver for the IP 4200 and that it also works with other select Canon IP printers, but I have not tried this.

---

### Post by Turin Turambar on 2006-11-20
Anyone willing to send me the turboprint.key? :p

---

### Post by rjpa on 2006-11-21
Yes, go to their homepage and buy a copy, the easiest way actually. That's what I did.

Cheers

---

### Post by mrdav1e on 2007-01-29
You can get a free version of the driver here:
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)
However it prints a logo at the bottom of the page until you buy the key.
Anyway, works for now.

---

### Post by penvzila on 2007-02-21
Does it also support the scanner part of the mp450?

---

### Post by mircione on 2007-05-23
Hi there.

I have the same printer. I download turboprint-1.94-4.ppc.tgz but i don't know how can I setup this?
I start to use Ubuntu couples days ago.

Best regards.

Mike

---

### Post by TheLeashedHare on 2007-06-29
Hi, from here [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) you can download and use Turboprint for linux, a high-quality printer driver system for Linux built on existing standards (CUPS or LPR(ng) printer spooler, ghostscript interpreter for Postscript) thus achieving easy integration and maximum compatibility with existing applications.
The Free Edition is for test or private use only - for business, governmental or educational use you need to purchase a professional license. So you can use it if you are a private.
There are packages for all platform, also DEB package!

---

