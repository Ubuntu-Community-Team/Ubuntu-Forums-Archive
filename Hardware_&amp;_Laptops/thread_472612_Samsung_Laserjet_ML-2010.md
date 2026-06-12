---
title: "Samsung Laserjet ML-2010"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by reginabally on 2007-06-13
I have the laserjet installed on a Windows XP machine and shared through the network.  I've installed the printer by specifying the host as "smb" and the printer as "machine_name/printer_name".

After finished installing, I tried to print a test page.  The printer property in my machine shows that the printer is ready.  Just that when it wants to send printer jobs to the networked printer, the status shown is: "Unable to connect to CIFS host".

Then I tried IPP/CUPS approach by specifying the IP address of the machine.  It gave me this status: Host "192.168.1.X" is busy".

I've tried most of the approaches posted on this forum but the problem can't be solved.

So, please help me with this problem.  Thank you very much!

P/S: Fyi, I'm running the Firestarter firewall, will it affect the printer sharing?

---

### Post by gowild00 on 2007-10-28
I believe the Samsung ML 2010 is a GDI printer which means the rendering is done on the host PC - I don't think they can be shared between XP and Ubuntu as I could not share them via a Linksys print server between 2 XP machines

---

