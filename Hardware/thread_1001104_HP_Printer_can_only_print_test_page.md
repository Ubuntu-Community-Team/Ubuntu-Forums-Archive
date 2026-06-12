---
title: "HP Printer can only print test page"
date: 2008-12-03
forum: Hardware
---

### Post by WildeBeest on 2008-12-03
I have a HP F4210 All-in-One printer that is only able to print the test page.

Can't print any documents or web pages.

I have the latest HPLIB installed.
The HP Device Manager works recognizing the printer, able to configure it, etc.

OS is Gutsy.

Anyone have any insight?

---

### Post by WildeBeest on 2008-12-04
ttt

---

### Post by endemoniada on 2008-12-04
Also having the exact same problem with a HP F2180 All in One, The only difference for me is that it was working fine for me in Gutsy, problems have only been occuring since I installed Hardy & then Intrepid (both fresh installs and not upgrades).

  Also everything works fine printing over a network from my windows machine using samba (Printer connected to Ubuntu Machine), but doesn`t do anything over a ubuntu to ubuntu network

 In Document Print Status Window the item being printed shows as processing for a 
couple of seconds and then changes to completed.

I Would also be grateful for any insights into how to solve the issue

---

### Post by WildeBeest on 2008-12-07
bump for an answer

---

### Post by Sulanino on 2008-12-21
Same problem.

Ubuntu 8.10
Using Turbo Print 2.06-1
Printer Canon Pixma MP530

Can Print test page from system-config-printer 1.0.5 and thats it.

When printing everything seems right. But nothing happends at the printer.
When opening Turboprint Printer Monitor after "printing" i get this error: Last job failed (0 pages) 'premature end of print data'.

Merry Christmas/Glædelig jul!

EDIT

/var/log/cups/error_log

E [21/Dec/2008:12:37:15 +0100] CUPS-Delete-Printer: Unauthorized
E [21/Dec/2008:12:38:40 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:38:47 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:38:47 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2008:12:42:01 +0100] Pause-Printer: Unauthorized
E [21/Dec/2008:12:42:06 +0100] Resume-Printer: Unauthorized
E [21/Dec/2008:12:42:06 +0100] Resume-Printer: Unauthorized
E [21/Dec/2008:12:51:45 +0100] Pause-Printer: Unauthorized
E [21/Dec/2008:12:51:50 +0100] Resume-Printer: Unauthorized
E [21/Dec/2008:12:51:50 +0100] Resume-Printer: Unauthorized
E [21/Dec/2008:12:53:10 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:17 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:18 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:20 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:20 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:20 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:20 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:25 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:26 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:27 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:28 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:30 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:30 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:30 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:30 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:31 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:32 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:33 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:35 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:35 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:35 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:35 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:36 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:36 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:36 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:36 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:38 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:41 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:42 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:42 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:42 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:42 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:43 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:43 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:43 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:43 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:50 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:52 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:52 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:52 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:52 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:53 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:53 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:53 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:53 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [21/Dec/2008:12:53:59 +0100] cupsdAuthorize: Local authentication certificate not found!

---

### Post by bkline on 2008-12-22
Same problem in Ibex.  Worked fine in Heron.

Print-Job: Unauthorized in cups error log.

---

### Post by bkline on 2008-12-22
Well, after a good deal of frustrated wrestling, I believe I have solved my problem.  Don't know whether this will work for the OP (or the others in this thread), but we can hope.

I had always installed printers using CUPS ([http://localhost:631](http://localhost:631)).  Out of desperation I deleted the printer in CUPS and went into System / Administration / Printing and re-added the printer.  Works like a champ now.

Hope this helps someone else.

---

### Post by fewjr on 2008-12-22
I am having the same problem also...test page fine....no print otherwise. I added the printer the usual way from System>Administstation>Printing. Its an HP Photosmart C4200. Your saying I should delete the printer and try again?

fewjr

---

### Post by bkline on 2008-12-24
> **fewjr said:**
> Your saying I should delete the printer and try again?

That's what worked for me.

---

### Post by trickytrickytricky on 2008-12-24
Similar problem here with an Olivetti anyway photo printer. After the progress bar tells me the printing is completed a printer icon appears on the top right of the screen with a balloon message. It tells me that my "printer may not be connected". Of course it is connected and it is switched on. Any ideas?

---

### Post by bkline on 2008-12-24
> **trickytrickytricky said:**
> Similar problem here with an Olivetti anyway photo printer. After the progress bar tells me the printing is completed a printer icon appears on the top right of the screen with a balloon message. It tells me that my "printer may not be connected". Of course it is connected and it is switched on. Any ideas?

Any of these help?

[http://ubuntuforums.org/showthread.php?t=849146]("http://ubuntuforums.org/showthread.php?t=849146")

[http://fixunix.com/ubuntu/516681-printer-may-not-connected.html]("http://fixunix.com/ubuntu/516681-printer-may-not-connected.html")

Or just google ubuntu "printer may not be connected".

You might also want to look at the output of dmesg.

---

