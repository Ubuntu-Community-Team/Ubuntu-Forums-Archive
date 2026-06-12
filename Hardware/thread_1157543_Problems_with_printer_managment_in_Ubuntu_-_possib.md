---
title: "Problems with printer managment in Ubuntu - possible bug"
date: 2009-05-12
forum: Hardware
---

### Post by spiralciric on 2009-05-12
Hi,
I have canon LBP3000 laser printer. I have downloaded both versions of driver from canon, version 1.6 and 1.8, and followed step by step instructions. I also checked all over the net for the solution, but found none.
My printer is identified, and status is fine, just it wont print. This is in detail what happens, and the steps I followed.
First I made sure that I have removed printer's spooler:
/usr/sbin/lpadmin -x LBP5000


Then, I installed these provided packages:
 # dpkg -i cndrvcups-common_1.80-1_i386.deb
 # dpkg -i cndrvcups-capt_1.80-1_i386.deb
 
 

I checked for driver version by:
 # dpkg -l | grep cndrvcups
and it was fine, 1.80


Then I restarted cups and registered:

 
/usr/sbin/lpadmin -p LBP3000 -m CNCUPSLBP3000CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
/usr/sbin/ccpdadmin -p LBP3000 -o /dev/usb/lp0

And started daemon:
 # /etc/init.d/ccpd start


In system/preferences/default printer my printer is set as default
In system/administration/printing there is LBP3000 with green check
I click on properties and I noticed that for driver it says 1.5 version. That was odd, but I tried nonetheless. I did print page, it said completed, but no printing occurred. I then tried to change Make and Model by clicking on the button to the right and chosing the right ppt file, since from select from database was only that 1.5 version driver that probably came with Ubuntu. I am using 9.04, so its a bit odd that it has driver so old.
In previous steps you noticed that in fifo0 I registered my ppt, and fifo0 is chosen, but still that 1.5 version, and printer wont print anything although status says everything is fine and printing jobs compleated.
It took me hours and hours working on this, but still no solution. If anyone could help, it would be great, if not, it would be good to state this as official bug.

---

### Post by bayvista on 2009-06-18
I have exactly the same problem on 8.10. All the instructions appear to work OK but the printer just refuses to print. (It works OK under Windows). I'm that desperate that I'd even consider paying someone to get this working.
The printer appears OK in CUPS GUI and everything appears normal. 

Any suggestions welcome.

---

