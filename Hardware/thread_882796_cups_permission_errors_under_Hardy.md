---
title: "cups permission errors under Hardy"
date: 2008-08-07
forum: Hardware
---

### Post by plato4me on 2008-08-07
Since upgrading to Hardy, I can't print.

Here's what I have currently.

Harware: an HP LaserJet 2300d connected to a Linksys PSUS4 print server.  

(This setup works perfectly with my macs and windows systems  It used to work with Ubuntu.)

My printer is set to:

lpd://192.168.1.104/myprintername

I'm using the LaserJet 2300 postscript driver.

I just tried to print the test page.  Nothing doing.  Here's what I have in the error log:

E [07/Aug/2008:08:34:33 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [07/Aug/2008:09:04:44 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [07/Aug/2008:09:04:50 -0600] CUPS-Add-Modify-Printer: Unauthorized

Can anyone help?

---

### Post by plato4me on 2008-08-07
Postscript:

The error log now has one more line:

E [07/Aug/2008:09:10:02 -0600] PID 8346 (/usr/lib/cups/backend/lpd) stopped with status 1!

Anyone have any idea what I should try?



> **plato4me said:**
> Since upgrading to Hardy, I can't print.

Here's what I have currently.

Harware: an HP LaserJet 2300d connected to a Linksys PSUS4 print server.  

(This setup works perfectly with my macs and windows systems  It used to work with Ubuntu.)

My printer is set to:

lpd://192.168.1.104/myprintername

I'm using the LaserJet 2300 postscript driver.

I just tried to print the test page.  Nothing doing.  Here's what I have in the error log:

E [07/Aug/2008:08:34:33 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [07/Aug/2008:09:04:44 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [07/Aug/2008:09:04:50 -0600] CUPS-Add-Modify-Printer: Unauthorized

Can anyone help?

---

### Post by plato4me on 2008-08-07
I reinstalled Ubuntu from scratch, did all the suggested updates, and tried again.

This time, I get the following error message:

E [07/Aug/2008:12:49:33 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [07/Aug/2008:12:49:52 -0600] [Job 1] No %%BoundingBox: comment in header!

This is really frustrating.  Everything else about Hardy works so well?  What's wrong with cups?

There surely has to be a simple fix.

---

### Post by plato4me on 2008-08-12
I have found what appears to be a workaround for this problem.

sudo echo "net.ipv4.frto = 0" >> /etc/sysctl.conf

sudo sysctl -p

I have absolutely no idea WHY this "fixes" the problem, but it appears to do so.  Now I can print using my local printserver (the linksys psus4).

Perhaps someone else will find this info useful.

---

### Post by baosheng on 2009-12-19
this solution doesn't work for 9.04 Jaunty Jacklope anymore. 

I tried it and got the error: 

error: "net.ipv4.frto" is an unknown key

---

