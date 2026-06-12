---
title: "Changing ink cartridges"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by marsopia on 2005-05-10
Hi people!

how can I manage to change ink cartridges or even to know ink level on a Epson 480?

Win drivers have some utilities that I  cant find on cups-gimp-print. I installed escputilis and foomatic, but I cant make them run. 

Untill now I used to go to XP to change the cartdriges, but I want Hoary to do that. ¿How do you people manage to change ink cartdriges?

---

### Post by jeremy on 2005-05-10
I don't know your model, but I am pretty sure that you can do it by holding down a button (on the printer) while turning it on, check the instructions.

---

### Post by marsopia on 2005-05-10
No buttons on printer... it works via software, thats why I'm asking.

Thanks for repying. Printers should have some buttons...

Mariano

---

### Post by jeremy on 2005-05-11
[http://esupport.epson-europe.com/ViewFAQ.aspx?lng=en-GB&ID=KB020016EN&data=A7B3DD960112ADED6105F1C2F657ABF021D725F78C211B0CE1EE95406950DE24](http://esupport.epson-europe.com/ViewFAQ.aspx?lng=en-GB&ID=KB020016EN&data=A7B3DD960112ADED6105F1C2F657ABF021D725F78C211B0CE1EE95406950DE24)
says, "Switch on the printer. The print heads will now move to the replacement position. If they do not move to a change position press the Red ink button on the printer". This is for putting the cartridges in for the first time, but maybe it is of help.

---

### Post by marsopia on 2005-05-11
Thanks jeremy, but I have no buttons on my printer.
I have now a good tip to relace my cartridges, but it seems quite primitve to shutdown the system, disconnect the printer, turn it on and chamge the cartridge...
it must be some software way...

how do you people who have Epson printers manage  to chenge cartridges?


Mariano

---

### Post by jeremy on 2005-05-11
I don't have an Epson, I have an HP. At least you CAN change the cartridges now, if not in the most elegant manner...

---

### Post by Swab on 2005-08-15
I'm having the same problem.   There is a utility called mtink which you can apt-get... the only problem is that it crashes every time for me.

---

### Post by kiwigander on 2005-12-19
I installed **mtink** (using Synaptic to apt-get it) and found that I could run mtink in a root terminal but not as an ordinary user.  

I've now got it to work by intalling a "custom launcher" on the panel and assigning it the command 

     **gksudo mtink**

Hope this helps.

---

