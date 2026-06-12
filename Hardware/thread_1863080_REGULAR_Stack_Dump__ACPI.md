---
title: "REGULAR Stack Dump ? ACPI ?"
date: 2011-10-17
forum: Hardware
---

### Post by MACE1 on 2011-10-17
I am running XUBUNTU with minimal applications on my new Foxconn NTA3500 using a 16gb SD card and 4GB ram. It runs fine for a few hours then stack dumps. 
Unable to handle kernal paging request at fffffffffffffff8
There used to be ACPI issues with BIOS's for these style of devices but that was 2-3 years ago so should be OK now !

Suggestions :confused:

e.g.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119050](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119050)

---

### Post by Redblade20XX on 2011-10-17
Can you post your Xubuntu version and the kernel number? :)

- Red

---

### Post by MACE1 on 2011-10-17
Installed from: xubuntu-11.04-desktop-amd64.iso
Will have to wait until tomorrow to get access to kernal info !
M

---

### Post by Redblade20XX on 2011-10-18
From your screenshot, your kernel is 2.6.38-11-generic. :) When you start the computer up, can you do a memtest?

-Red

---

### Post by MACE1 on 2011-10-19
Using the latest MemTest86+ 4.20 I could get, I did 7 full passes with No errors - Nor did the unit crash or re-set.

Not sure if this actually tests ALL ram as I don't know if its 32bit (Probably) so can not see full 4096 and as the test is itself in memory....;)

---

### Post by Redblade20XX on 2011-10-19
The installation is 64 bits but hmmm only 4 gb... Can you check your bios and see how much ram is detected? :-k  Next time when there is a crash, do you mind recording the time it crashed and post the kern.log file located in /var/log upon reboot? Also does this happen everytime you leave the computer on for a couple of hours?  Did this problem recently started to occur and if it did, was there any significant changes made to the system? Sorry for the many questions, need to get alot of info for debug! :)

- Red

---

