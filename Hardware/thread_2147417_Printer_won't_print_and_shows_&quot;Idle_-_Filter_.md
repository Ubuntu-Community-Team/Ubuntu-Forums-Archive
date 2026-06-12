---
title: "Printer won't print and shows &quot;Idle - Filter failed&quot;"
date: 2013-05-21
forum: Hardware
---

### Post by AlanQ on 2013-05-21
I've just had this problem in Mint14 (which is basically Ubuntu something with extra bits).

**Description of problem:**

Printer doesn't print.

System > Administration > Printers

Double click the printer.

Under Settings the 'Printer State:' is 'Idle - Filter failed'.

**Solution:**
Reinstall the printer :)
Under System > Administration > Printers
Click '+ Add' and follow the instructions.

**Cause:**
I don't know the cause of the problem, but this solution worked for me.

**UPDATE**
Unfortunately the problem is back after a reboot, so you have to re-install the printer again...

---

### Post by Enjay_Linux_Initiative on 2013-10-19
AlanQ did you manage to get rid of this error. If yes can you please share the information on how to deal with filter failed error. I am getting the same error after installing ubuntu 13.04 on my system.

---

### Post by AlanQ on 2013-10-19
Hi  Enjay

Unfortunately not.

My fix is good enough for me to live with the bug.

When I go to print, I now have three installations/instances of the same printer.
When one fails with the silly error, I just use one of the others.

I have found that printing PDFs from 'Document Viewer' (Atril/Evince) is reliable.
The error occurs when printing from other applications.

So, if an application has already 'killed' two of my printer instances, I "Print to File" (=PDF) and then open and print the PDF.

There's another bug I've noticed which is where the printer shows as 'turned off or unplugged'.
Then I have to go to System > Administration > Printers ,  select Policies , and re-tick 'Enabled'.
I've no idea why this one happens either.

My printer is an *HP Officejet 6500A Plus*.
It's the one that takes longer to warn up than the Deathstar preparing to destroy a planet!

Fortunately I don't do much printing, and I have so many years experience with documents that I can always (so far) work out a fix for the myriad other bugs as well. Don't know if it's bugs in the printer, bugs in the HP software, or bugs in the more generic side of the printing software.

HP always used to be so Linux-reliable.

---

