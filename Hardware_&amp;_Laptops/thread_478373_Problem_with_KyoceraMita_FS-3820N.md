---
title: "Problem with KyoceraMita FS-3820N"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by stuppaz on 2007-06-19
Hi, I am newby with Ubuntu. I used a bit fedora 7.
For work I need to use a network print.  
With fedora 7, I simple add a printer using "AppSocket", specifying the socket address like "socket://xxx.xxx.xxx.xxx:9100" and all was ok.
I have thought to do same with Ubuntu 7.04 (Feisty Fawn) but it does not work. 
First I add printer using "System/Adminsitrator/Printer" and I was not able to print.
After that I used directly the cups manager: "htt://localhost:631", with the same results.
I thought that the problem could be on the permits. So I used the following command:  "sudo gnome-cups-manager", but nothing to do.
The printer is added but it doesn't work.
In the log (cups log: /admin/log/error_log ) I can read things like that:

E [19/Jun/2007:14:29:55 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Jun/2007:14:29:58 +0200] cupsdAuthorize: Local authentication certificate not found!
E [19/Jun/2007:14:29:58 +0200] CUPS-Delete-Printer: Unauthorized
E [19/Jun/2007:14:30:48 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:14:31:55 +0200] [Job 18] No %%BoundingBox: comment in header!
E [19/Jun/2007:14:33:44 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:14:33:54 +0200] [Job 19] No %%BoundingBox: comment in header!
E [19/Jun/2007:14:54:11 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:14:54:21 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:14:58:45 +0200] CUPS-Set-Default: Unauthorized
E [19/Jun/2007:14:59:20 +0200] [Job 22] No %%BoundingBox: comment in header!
E [19/Jun/2007:14:59:30 +0200] [Job 23] No %%BoundingBox: comment in header!
E [19/Jun/2007:14:59:38 +0200] [Job 24] No %%BoundingBox: comment in header!
E [19/Jun/2007:15:02:57 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:15:04:48 +0200] CUPS-Delete-Printer: Unauthorized
E [19/Jun/2007:15:06:26 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:15:06:52 +0200] [Job 26] No %%BoundingBox: comment in header!
E [19/Jun/2007:15:09:18 +0200] CUPS-Add-Modify-Printer: Unauthorized
E [19/Jun/2007:15:09:24 +0200] [Job 31] No %%BoundingBox: comment in header!

is there somebody can help me. 

Thanks for answer !

---

### Post by stuppaz on 2007-06-20
Is there nobody that had the same problem ?

---

### Post by stuppaz on 2007-07-20
I risolved the problem.
I add the user that I use to connect to lp group,

I restart the service and it worked !

---

