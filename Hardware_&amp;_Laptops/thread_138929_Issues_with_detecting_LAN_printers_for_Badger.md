---
title: "Issues with detecting LAN printers for Badger"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by minghai on 2006-03-02
Hi all,

    My little office LAN network of 4 PCs each have their own printer (some laser, some colour, some multifunction) attached to them individually via USB ports.  When they were all running Hedgehog, each PC could see all the other printers once LAN detection was activated.  Since I've upgraded to Badger, from each PC, I can only see the printer attached to it and not those attached to other PCs.  Is there something else I need to set or do other than activate LAN detection from the printer dialog box?  Thank you!

Ming Hai

---

### Post by minghai on 2006-03-03
Ok, got the solution from another thread on the forum :-

Edit the /etc/cups/cupsd.conf file. 
Find the line "#Port 631" and remove the #. About 2 lines down there will be a line "Listen 127.0.0.1:631". Put a # in front of this line to comment it out. Next find the line "<Location />" and after the line "Deny From All" add a line "Allow From @LOCAL"

save the file and restart cups:
sudo /etc/init.d/cupsys restart

---

