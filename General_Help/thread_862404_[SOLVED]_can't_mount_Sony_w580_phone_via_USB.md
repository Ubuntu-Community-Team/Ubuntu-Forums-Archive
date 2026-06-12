---
title: "[SOLVED] can't mount Sony w580 phone via USB"
date: 2008-07-17
forum: General Help
---

### Post by kedmond on 2008-07-17
Hey guys,
    I am using Ubuntu 8.04.  I have a Sony Ericsson w580i cell phone.  I've plugged it into the computer in the past, selected File Transfer Mode, and the "PHONE DISK" would mount.  This was a while ago, when I was using 7.10.  Lately, however, I just can't get it to work.  I plug it in, and "lsusb" doesn't show any Sony devices:

Bus 004 Device 004: ID 059f:0951 LaCie, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:2003 Dell Computer Corp. 
Bus 001 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000  

and fdisk -l doesn't show my phone either.  I have no idea what to do.  Thanks.

-kedmond

---

### Post by kedmond on 2008-07-17
Nevermind...while the phone was plugged in, I popped out the flash memory chip in the phone, and then slid it back in again.  It mounted right away.

-kedmond

---

