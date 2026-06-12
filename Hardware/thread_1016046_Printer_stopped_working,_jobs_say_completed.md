---
title: "Printer stopped working, jobs say completed"
date: 2008-12-19
forum: Hardware
---

### Post by jema on 2008-12-19
Title says it all really. I have a epson CX11N and it has been working fine, it is installed twice and both were working. All of a sudden whilst I can still print a test page, jobs I submit come up as completed but nothing prints.

---

### Post by cariboo on 2008-12-19
Go to [http://localhost:631](http://localhost:631) and check the logs to see if there is anything obviously wrong. You could try to print a test page from the cups interface, to see if it works.

Jim

---

### Post by jema on 2008-12-19
I see :

E [19/Dec/2008:15:38:52 +0000] cupsdAuthorize: Local authentication certificate not found!
E [19/Dec/2008:18:38:22 +0000] DNSServiceRegister failed with error -65537
E [19/Dec/2008:18:38:22 +0000] DNSServiceRegister failed with error -65537
E [19/Dec/2008:19:29:33 +0000] CUPS-Add-Modify-Printer: Unauthorized
E [19/Dec/2008:19:33:08 +0000] cupsdAuthorize: Local authentication certificate not found!
E [19/Dec/2008:19:33:08 +0000] cupsdAuthorize: Local authentication certificate not found!


in the printer log, and I saw:

Dec 19 19:29:08 localhost python: io/hpmud/jd.c 84: unable to read device-id 
Dec 19 19:29:08 localhost python: io/hpmud/jd.c 625: invalid ip 192.168.0.190 
Dec 19 19:29:08 localhost python: hp-makeuri[7393]: error: Device not found
Dec 19 19:29:08 localhost python: hp-makeuri[7393]: error: Device not found
Dec 19 19:29:11 localhost python: io/hpmud/jd.c 84: unable to read device-id 
Dec 19 19:29:11 localhost python: io/hpmud/jd.c 625: invalid ip 192.168.0.190 
Dec 19 19:29:11 localhost python: hp-makeuri[7396]: error: Device not found

in the syslog. That was after I reinstalled the printer. It still did not work, so to see if I got the same error I printed again on the original printer install and it worked :confused: it has continued to work since.

It is a network printer on 192.168.0.190

---

### Post by RockDoctor on 2008-12-19
Same problem with my HP PSC-2110. Using Jaunty Jackalope alpha updated as of 10:00 AM CST. No problems with my Intrepid Ibex install

---

