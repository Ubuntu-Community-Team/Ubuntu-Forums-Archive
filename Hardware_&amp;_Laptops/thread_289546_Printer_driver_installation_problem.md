---
title: "Printer driver installation problem"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by nomad111 on 2006-10-31
hey all,
just installed 6.10 yesterday and today was trying to install my printer driver. i was following the instruction of the printer manufacturer's site when i stumbled upon a problem trying to install the printer's cups wrapper driver. i was hoping that someone could help me solve this problem.

Regards,
nomad111


prodigy@prodigy-laptop:~/Desktop$ sudo dpkg -i --force-all cupswrappermfc620cn_1.0.0-1_i386.deb 
(Reading database ... 90385 files and directories currently installed.)
Preparing to replace cupswrappermfc620cn 1.0.0-1 (using cupswrappermfc620cn_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
Unpacking replacement cupswrappermfc620cn ...
Setting up cupswrappermfc620cn (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC620CN
 * Stopping Common Unix Printing System: cupsd                           [ ok ] 
 * Stopping Common Unix Printing System: cupsd                           [ ok ] 
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!

---

