---
title: "Printer problem -Ink cartridge complication."
date: 2009-04-18
forum: Hardware
---

### Post by MadMax2 on 2009-04-18
I couldn't (still can't) get my hp deskjet 3325 to print. It went through all the printing movements but didn't print (pretended). The one function it would do was head align (it printed the marks).
 It printed on a windows laptop so ink didn't appear to be the problem.

The supported printers page said it worked (mostly).
[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)
running hp-check showed missing [bits] but looking in synaptic package manager showed them to be either installed or the names didn't match. I wondered if choosing the wrong one would produce a conflict.

My scanner wasn't supported.

I decided to buy a second hand Multi Function HP PSC 1500 (Scanner, printer and fax) which according to the supported printers page works "perfectly".
I bought a second hand one because i was told the new ones wouldn't be supported. ?
Meanwhile I got a free copy of Ubuntu 8.10 from the computer shop and reinstalled (in case I has messed something up).

The scanner worked. 

In Printer properties print self -test page and Clean Heads is grayed but I found the commands 
[http://hplipopensource.com/hplip-web/tech_docs/man_pages/index.html](http://hplipopensource.com/hplip-web/tech_docs/man_pages/index.html)

(hp-align and hp-clean) and installed hp tool box via synaptic package installer. [I don't see a command for print self test page?]

the printer wasn't printing black. 
We had tested the printer on my wifes vista laptop not noticing that (in fact) the web recipe she printed was actually bluish (not black) and assumed it must therefore be a software problem on my desktop, also hp-check revealed " 12 errors and/or warnings".

Tool box claimed the ink level was very low (I read that refilled cartridges may not show as  being full). I didn't want to buy a new cartridge if there was still a software problem as a cartridge would cost more than my second hand printer.
I injected more ink into the cartridge through a hole at the top but wasn't sure if it was going in (as it was coming out the top) or not, or if I had the correct hole.
Later I saw on You Tube how to clear the heads in boiling water. After dipping the cartridge in boiling water and drying it, it printed. 
[http://www.youtube.com/watch?v=mogfeT5YYco&NR=1](http://www.youtube.com/watch?v=mogfeT5YYco&NR=1)

The HP psc 1500 prints a page with lines when first switched on until you (sucessfully) scan it and let it do a head align.

The print align page wasn't clear the first time but was the second time. I just switched it off and on and it didn't print a page (indicating that the head alignment routine worked).

:D

I had been told that if i buy a print server I can connect most scanners and printers to it; it will manage the priners etc and linux only has to deal with the server (which is a work around)?

---

