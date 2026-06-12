---
title: "APIC Trouble with Toshiba Satellite A100"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by cal-lito on 2007-07-20
Been having trouble with the latest Ubuntu, with latest updates installed, on my Toshiba Satellite A100 laptop.

When booting, I get the bug:  8254 Timer not connected to IO-APIC

I suspected this to be the cause of constant desktop freezes.  I can *rarely* 
work for more than 5 minutes without the computer freezing.  The desktop seems 
to freeze when I move the mouse at a time when the processor is busy  (for 
instance, if I move the mouse while Firefox is rendering a page, or scroll very 
fast on pretty much any application).  It's *not* specific to any particular application; 
it freezes with OpenOffice, with Thunderbird mail, with Firefox...  Even when 
simply dragging a terminal window around, or resizing it. 

At first, it just freezes the mouse --- I have keyboard control, and I can close the 
windows with Alt-F4, or type commands on a terminal...  But if I try to log off, or 
do Ctrl-Alt-F1 to go to a pure-text interface, then the whole thing freezes to the 
point where the only recovery is to power it off.

I disabled APIC with the noapic option for the boot loader;  the message when 
booting (the Timer not connected...) disappeared --- the problem seems to have 
disappeared (worked for almost two hours without having to power off and on 
again due to the computer freezing).....  BUT ...  networking does not work  (as 
if the laptop had no network device at all --- everything fails, both wired and 
wireless networking).

Any similar experiences?  Any way to get around the bug, or to make it work with 
the noapic boot option?

BTW, I flashed the laptop BIOS not long ago --- didn't change a thing.

Thanks,

Cal-lito
--

---

