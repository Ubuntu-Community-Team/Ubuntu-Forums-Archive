---
title: "problems with HP printer"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by philsf on 2006-07-03
Hello,

I am having some serious problem in configuring my HP OfficeJet 4225 printer in linux, the problem being it doesn't use black ink when printing.

My (3-)color ink has almost died on testings, and I just got a brand new (original hp) black cartrigde, but it onlye prints in faint (almost vanishing) yellow. 

This same thing happened to me previously to installing kubuntu, both with Debian Sarge, and Etch (both up to date). I still have an (up to date) Etch, and a Windows XP for testings on a separate PC. Printing is fine on windows, which probably excludes hardware problems.

Facts: in this kubuntu I firstly tried the traditional way of configuring the printer with the main tool (which I supose to be a front-end to kprint), with HPLIP from kubuntu dapper. The PC correctly finds the USB printer, and creates the hp:// CUPS backend. HPs tool programs seems to work just fine, showing ink levels and managing queues and jobs. It's just the black ink that 
don't come out... I then tried purging all hplip packages, and compiling the last version (1.6.6), following step by step the instructions. Same result.

On linuxprinting.org, this model (actually 4200) reports as working "mostly", but it should mean IMHO that it could print with basic color cartridge. I don't need photo quality. On that site there is a report that it worked out of the box on a Mandriva linux, so it should work somehow. I just can't find out how.

Any suggestions?

regards
FF

---

