---
title: "Z52 revisited"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by borisattva on 2005-12-31
i was trying to configure my printer under this fresh install of ubuntu.
it appeared that the machine detected it just fine, but when it came time to set it up, the immediately displayed portion only mentioned z42,43,51 and 82.

remembering that 52 and 42 were essentially the same with speed being the only difference, i selected that and ran test print. the paper woudl start feeding with a strange noise and stop at the last few lines. holding the paper in. canceling the job would force it out. i proceeded to also try using the 51 and the 82 drivers to similar results.

finally i discovered that z52 and the rest were listed as "LEXMARK Zxx"
(should probably fixed and made more uniform in the main packaging, if possible)
and tried using that, which in turn just times out.. 

i tried removing the printer from listing, completely turning off it and the pc and restarting and reinstalling to the same result. is it possible that using the inappropriate drivers i messed something up in the system that will need manual plucking out, or worse yet, messed up my printer?

---

### Post by Sef on 2006-01-03
Lexmark has drivers for the Z52, but only for Mandriva, Redhat, and Suse.  Maybe someone else can tell you how to get those downloaded to a deb system.

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:292:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:292:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::")

---

### Post by borisattva on 2006-01-03
well it apears Ubuntu itself has drivers for z52 (and by the way i have alreday seen the ones on lex's website) but i suspect the ones in ubuntu are already the adapted ones, as there simply dont apear to be any other on the web.

what i'm conserned about is whethere or not the previous installs i made could have affected the system and rendered printer useless with this instance of ubuntu

---

### Post by borisattva on 2006-01-11
Today i had to reinstall breezy after repeated and failed dapper attempts, and configured the printer properly form the 1st try. It worked perfectly.
Printing is rather slow and quality leaves alot to be desired for, but it works.

So looks like i was right - my previous attempts at selecting and configuring another printer somehow contaminated the system and even afer removale of the instal and 'reinstaling' still did not get rid of the problems.

Unfortunatley I cant provide a useful method on cleaning up the system with out a full reinstall just yet, but hopefully this will give an idea to other forum searchers inthe future into the cause of the problem.

---

