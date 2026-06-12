---
title: "HP LJ1020 strange printing problem"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by tribunal on 2008-01-18
Hi all!
I have bought HP LJ1020, installed it using HPLIP and now I have a very strange problem
When I pring anything in A4, it prints ok, except one fact:
For each page to print it need 2 pages to move through printer:
1 page to print and next empty page is going through priner
So, for example to print 10 pages of text I need 20 pages to be ready :confused:

---

### Post by azad on 2008-01-18
Hi, I have a HP Laserjet 1020. Its on a Windows print server with 9 Ubuntu boxes and 4 XP boxes using it over the network. Never had any issued with it.

It seems to be a problem with the roller inside the printer.

At first remove the printer (System > Administration > Printing, Select HPLaserjet and delete). Then, install it again. See if problem persists. 

Try using the printer with WinXP/Vista and if the problem persists, you can be sure that its the printer's fault.

If it the printer that's faulty, get it replaced.

---

### Post by tribunal on 2008-01-18
I have found, where is a problem
In Windows everything is ok except one moment: last string is not printing till the end (several pixels are cut)
In Linux it is the same, but these pixels are printed on the next page!! (So, I see it as empty page, usually)
I have heard about this problem of several HP-printers, but I don't know, how to solve it in Kubuntu

---

### Post by tribunal on 2008-01-18
I have fixed it! :)
Drivers from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) are a good solution

---

### Post by 11hjpphty76lkjj on 2008-01-25
This page after printing in A4 problem will be fixed in the next release of HPLIP.   Sorry about that.  Aaron

---

