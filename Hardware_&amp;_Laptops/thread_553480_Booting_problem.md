---
title: "Booting problem"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by satimis on 2007-09-17
Hi folks,


Ubuntu 7.04 server amd64
Mobo - ASUS M2N-E


In these few days I'm suffering following problems.


1)
Each day on 1st booting the PC, it fails with the warning of "CMOS Checksum error - Default load" popup

I have to start BIOS pages and then "Save and Exit without Saving".  I did not change anything there.

Reboot the PC then it works.


2)
The clock is not accurate slowing down.  After running "sudo date -s "09/17/2007 23:51:00" it works correctly again.  However how long does it run I'm not aware.  Maybe after a reboot I have to run "date" again.


Please advise where I have to look at?  I have changed the battery.

TIA


B.R.
satimis

---

### Post by w4ett on 2007-09-17
Did you save your changes in bios  (F10 generally) before rebooting?

---

### Post by satimis on 2007-09-17
> **w4ett said:**
> Did you save your changes in bios  (F10 generally) before rebooting?
I haven't changed BIOS settings for long time.  The funny is I have to start BIOS at 1st boot and select "Save and Exit" to fix the problem.  Actually I haven't made any change there.

satimis

---

### Post by w4ett on 2007-09-17
Sounds like you need to enter the bios setup and reset the Master System Clock which is maintained in the CMOS.....changing the battery without setting the clock will maintain the system in an error state at boot.

---

### Post by satimis on 2007-09-17
Hi folks,


I changed the battery forgetting to change the "Time" and "Date" on BIOS.  Just reset them.  I'll come back to the forum if problem reoccures.  Tks


satimis

---

### Post by w4ett on 2007-09-17
no problem......Good Luck

---

