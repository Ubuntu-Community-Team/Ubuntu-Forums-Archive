---
title: "Slow printing on HP laserjet 1000"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by B7may on 2006-03-14
I have a Breezy 5.1 machine that acts as my file server and print server.  I havea HP laserjet 1000 connected to this machine.  It took me many hours to actually get the HP printer to work, I ended up having to download special files.  Now it prints fine, but is extremely slow.  When I try to print to it from a networked computer running windows XP, it sometimes takes 5 minutes to print the document.  (I had an HP laserjet 1100 hooked up, and it worked great.  Buth the printer broke, so I am left with the 1000).  Any ideas on how to speed this up?

Thanks
Brian

---

### Post by seedsgrow on 2006-03-22
I'm sorry I can't help you with your problem, but maybe you can help me with mine. I can't get my LaserJet 1000 to print in Breezy. I have installed this printer several times before in Linux and always had to install the firmware manually. Despite the documentation for the foo2zjs driver saying this is no longer necessary, the printer's behavior and your statement about having to download special files makes me doubt this. Did you download the Windows driver from the HP site, extract a file called sihp 1000 from it, and place the file in a folder where the printer could find it? If so, what is the pathway to the folder where you put the file? If not, what did you do?

Edit: I have solved my problem by downloading the foo2zjs driver from the developer's site, compiling it, and running a udev/hotplug script included with it. Running that script was what finally got the firmware installed properly.

---

