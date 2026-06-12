---
title: "Ideal hardware setup for Ubuntu Webserver?"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2006-10-16
I'm trying to set up an intranet here at work, and I want to use Ubuntu because it is so easy to manage.  I want to set up a server that we won't have to upgrade for a while (max 150 users accessing the server, probably only about 50 at a time on average).

I'm thinking of an AMD 64 X2 based system, with at least 1GB of RAM, but I'm having trouble finding a good motherboard.  I've only ever used ASUS and I've heard about more and more Asus boards having problems with working with linux.

I do not want to have to compile a custom kernel, and all I need it to do is run off of some SATA 3Gb/s drives and run 24/7 for about 4 or 5 years.  (I had an old Pentium 2 that ran Ubuntu Warty for about 2 years before we migrated it to a true server, so I don't feel the urge to spend thousands on simple intranet if a $500 PC will work.)

Any advice?

---

### Post by sitedesign on 2006-10-16
We have used Ubuntu on several Dell servers and considering you only have about 50 users at a time, depending on what they are doing (web based - say PHP and MySQL) then a basic Xeon unit with 1GB RAM and a scsi HDD should do perfect, even a SATA should surfice is cost is an issue.

---

### Post by OneSeventeen on 2006-10-16
Since the organization is a not-for-profit, I'm having a hard time convincing them to purchase a server-class machine for the intranet, but I've assembled a machine from dell for about $1,000 which should definitely do the trick.  It only has a gig of ram, but if Ubuntu will run nicely on a dell server, then that's all I need to know.

We tried installing it on a Gateway server once and the obscure RAID controller and network adapter they used kept the server from being useful.

---

### Post by sitedesign on 2006-10-17
The Dell servers that I have tried are the SC400, SC420, SC430, 1420SC.

All in IDE, SATA and SCSI set-ups which work fine.

Since the 830 and 1430 use the same controllers they should be good too. I assume you won't be getting higher end than that for $1000.

Let me know how it goes.

You could always build your own by checking the hardware compatibility for the disk controller first (main install stoppers).

Let us know how you get on. Also don't forget that most of the Dell kit is cut down versions of the real thing, such as the SCSI controller is not as per the Adaptec original, missing several controllers and connectors etc. Your own built system would probably give much more punch for your buck.

---

