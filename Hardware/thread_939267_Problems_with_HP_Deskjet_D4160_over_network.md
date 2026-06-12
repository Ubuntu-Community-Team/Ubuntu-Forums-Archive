---
title: "Problems with HP Deskjet D4160 over network"
date: 2008-10-05
forum: Hardware
---

### Post by clk99 on 2008-10-05
I have a network with a desktop running XP and my laptop running Kubuntu 8.04.  I just got a Deskjet D4160 and hooked it up to my Windows machine.  Everything works great; I can print and all that.  I'd like to be able to print from my laptop, though, because I use my Windows machine more as a server and usually don't have any peripherals (including a monitor) hooked up to it.

So I go to System Settings -> Printers -> Add, next, check SMS shared printer, next, next, and interestingly when I try to scan for it it doesn't show up.  But I know where it is and manually type it in.  On the drivers page I can't seem to find anything for HP Deskjet D4160 or similar.  I've tried just choosing some Deskjet drivers and by doing this I can successfully send a test page to my print queue on the Windows machine, but the status usually goes from Spooling to Printing and nothing ever comes out.  

Is there an option on the driver I can choose that will be friendly to my new printer?  Is there a specific driver for the D4100 series that I can't find?  Is there some other way of doing this?  I've tried using the HPLIP toolbox but it's scanner can't find the printer either and I'm not sure how to manually type in the workgroup/host/printer in that program.

Thanks for any help.

---

### Post by clk99 on 2008-10-06
Still no luck.  According to another thread, there should be or there used to be an option for the Deskjet D4100.  I must just be missing something.  Does anyone else have this listed in their available drivers when they go to add a printer?

---

### Post by clk99 on 2008-10-09
bump

---

### Post by cariboo on 2008-10-09
Have you tried hplip-gui it is available in the repositories, you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

One other thing to make sure of is that you have your printer shared correctly in windows. Just right-click on the printer and select sharing.

Jim

---

### Post by clk99 on 2008-10-09
Yes, I've tried hplip-gui (HPLIP Toolbox) as said in my first post.  The printer must be shared correctly if I'm able to send data to the print queue on the other computer. I'm almost certain it's a driver issue, I just can't figure out which driver I need and how to get it going since the D4100 series doesn't show up in the list.

---

### Post by clk99 on 2008-10-09
I wonder if anyone running 8.04 could let me know if they see the drivers for the Deskjet D4100 in the list of drivers in the add printer wizard.  The poster of [this](http://ubuntuforums.org/showthread.php?t=312743&highlight=d4100) thread talks about having an option for it, but that thread is from 2006.  My problem is similar to his, except that I can't actually see the printer as shared (I have to enter the location manually) and I can't find my printer in the list and all he had to do was disable bi-directional printer, which I tried to no avail.  I'm quite lost.

---

