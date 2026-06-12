---
title: "Where to find and install PARPORT_PC"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by robert_bb on 2009-09-06
Updated 9/20/2009
While I see that several others individuals have looked at this document, but none have been able to post a response to help, I decided to post the answer to the problem which I was able get.

Using the terminal mode which is available under accessories, type:
sudo parport_pc

This will load the parport_pc module, but only for this session.  To get this module to load each time that you start your computer go into terminal mode and you will need to edit the file /etc/modules.  To do this type:
sudo nano /etc/modules

Then one a new line type:
parport_pc

save the file by overwriting the existing file.  Now, each time that you boot UBUNTU, this module will be loaded and you printer should be visible to UBUNTU.

Hope that otheres find this information helpful.



----------------------------------------
I am new to XUBUNTU and have it installed and running on an old Dell Inspiron 350.
However, I cannot get my printer on LPT1 recognized.  When I go to the new printer area, the system only wants to look for serially connected printers.

I did find the bug notice on PARPORT_PC, but I don't seem to be able to find out where to get this code or how to install it.  Remember, this is my first time using this system and everything is new to me.
THANX

---

