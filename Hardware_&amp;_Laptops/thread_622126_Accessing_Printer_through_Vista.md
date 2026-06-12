---
title: "Accessing Printer through Vista"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by jellystones on 2007-11-24
Hi,

My problem is that I cannot access the printer shared by Vista. 

I know it is shared properly because I have 3 Windows XP machines in the house that can see and use the printer.

Here is what happens when I try with Ubuntu Gutsy:

1) Click on System-.Administration->Printing

2) Click on "New Printer" and select "Windows Printer via Samba"

3) I click on "Browse" and in the list the Vista computer that is sharing the printer shows up.

4) If I click on "expand" arrow beside the Vista Computer, it shows nothing (as if the computer doesnt have a printer to share).  The "OK" button is grayed out, and the only thing I can click is Cancel.


Any ideas?

---

### Post by Phurious on 2007-11-24
Are you able to map to a folder share on the Vista workstation from the Ubuntu machine?  It sounds like a credentials issue. 

To test:

Share a folder on the Vista machine.  On the Ubuntu box, go to Places > Connect to Server.  Where it says "Service Type" use "Windows Share".  Don't forget to enter the username for the Vista box and the workgroup (in the Domain Name field) the Vista box resides in.  You can leave the rest blank, then connect.  If you are prompted for a password enter the password for the username supplied.

If that works, try mapping the printer.

---

### Post by jellystones on 2007-11-24
Is there a difference between your method, and the method I use to connect to a share (my way I just click Places->Network and connect to the Vista shares from there)

Using my way I can connect to the Vista folder share,

BTW how would I map the printer?

---

