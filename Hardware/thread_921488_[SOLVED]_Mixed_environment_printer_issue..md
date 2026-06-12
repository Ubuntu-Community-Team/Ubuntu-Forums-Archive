---
title: "[SOLVED] Mixed environment printer issue."
date: 2008-09-16
forum: Hardware
---

### Post by thegreatleslie on 2008-09-16
I have had an all Windows environment in my home until this past weekend when I decided to load Ubuntu on my aging Dell i8600 (8.0.4.1).  On my network, I have a Brother HL-2070N printer that has worked flawlessly among my 2003 Server, XP and Vista systems.

I was able to successfully get the printer installed using the drivers available on Brother's site and some of the detailed instructions I found on this forum.  I have run into a big problem, however.

It appears that, let's assume I just turned the printer off and on, whenever a system prints to that printer now, that OS type (whether it be Windows or Linux) becomes the only OS type that continue to print.  If I print a test page from Ubuntu, none of my Windows systems are able to print until I reset that printer - then their print jobs go through - and vice versa.  Also, once the printer goes to sleep, NO OS is able to print.  I can ping the printer, but all systems error saying it is not available.

This printer worked fine right up until I installed it on Ubuntu.  It was installed using the CUPS interface.  What could be causing this?  I've tried everything I can think of short of resetting it to factory defaults and starting over.

---

### Post by thegreatleslie on 2008-09-17
Thought I would update this since I found my own solution.

Apparently my printer had an address that was reserved within my backup VPN server's address range (printer was 192.168.1.50 and VPN backup server IP range was 50-54, but should have been 51-54).  This confused WINS.  I guess I wasn't thinking when configuring the backup server since I did it recently.

Anway, I changed the IP of the printer to 192.168.1.25, fixed the VPN backup server range, removed the entries in WINS, cleaned some ARP caches and all is well - working as it should.

Probably not something that will happen to anyone else, but you never know.

---

