---
title: "HPLIP doesn't print?"
date: 2010-10-20
forum: Hardware
---

### Post by gfunkdave on 2010-10-20
Hi all,

I'm hoping someone has a brilliant idea here. I'm running Maverick and I can't get it to print to my HP Color Laserjet 1312 MFP. hp-setup sees and installs the printer just fine (including the plugin). When I try to print a document or test page, it says it's printing. Even the printer's display says "Printing Document"...but nothing happens.

Everything works fine when printing from my Windows machines.

The results of hp-check -r are that no errors were found. hp-check without any arguments results in a slew of compile-time errors. I'm just using the package as downloaded from the repositories.

Can anyone help me out here please? Thanks!

---

### Post by gfunkdave on 2010-10-21
As an update, I seem to have figured something out, but I'm not sure what it means. After updating the printer's firmware, if I add the printer via System-Admin-Printing, I got it to work by using the print queue that my wireless print server presents.

My wireless print server is a DLink one that has four USB ports and one ethernet port. I have had the printer connected to the ethernet port, in which case the print server acts as a pass-thru wireless bridge. Windows machines print just fine to it; Ubuntu says it's printing, the printer's display says it's printing, but nothing prints.

I also tried plugging the printer in to the print server via USB, and manually creating a new printer in Ubuntu with <print server's IP> and the port of 9103. 9103 is the port that the print server assigned to the printer's USB connection. Under this setup, I can print.

I would really rather it just work through ethernet. But HPLIP's hp-setup program, which sees the printer's ethernet connection just fine, refuses to print. I also cannot scan through it.

Any help? I don't think there's a problem with the print server since ethernet printing works fine under windows, and USB printing works under both Windows and Ubuntu. I would like to be able to scan, however.

Thanks!

---

