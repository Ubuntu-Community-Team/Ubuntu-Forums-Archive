---
title: "ink nozzles of Epson l3150 seem to be clogged"
date: 2022-12-03
forum: Hardware
---

### Post by ulissipus on 2022-12-03
Good Morning! I didn't use my Epson L3150 for colour printing for a while and now the printer only works - perfectly - when printing in black and white. The ink cartridges are nearly full except the black ink cartridge. I think the nozzles must be clogged or dried. I've already tried cleaning using the printer's cleaning key and also via the desktop using escputil -c . In both cases the test page comes out flawlessly in black and white. But in color, practically nothing comes out.

Any suggestion as to how to do a thorough cleaning of the ink nozzles?
No support from Epson for linux, of course.

Running Ubuntu 22.10, by the way.

---

### Post by TheFu on 2022-12-04
Ink dries out and the fix is to buy a new cartridge.  After seeing that happen every time I wanted to print, I got a laser printer and never had the issue again.  Toner lasts years and color laser printers aren't THAT expensive.  A $150 color laser printer will start being cheaper than an inkjet after just 3-4 ink cartridges dry out ... which is usually after 6 months or less time, IME.

If you've been refilling the same cartridges, those wear out too, usually after about 2 yrs, IME.

Both inkjets and laser printers seem to release toxic chemicals into the air with the laser printers being worse, so just leave the room for a few minutes when printing.  I only print about 40 pgs a year, so I'm not too worried.

---

### Post by mIk3_08 on 2022-12-04
In my brother printer/scanner the printer head never dries out due to the printer system when it is not use it automatically cleans the head printer. Its just that the printer is not allowed to be turned off because the system needs it for automatic head printer cleaning. Though it consumes power but then the printer head never dries out. I only use printer few time a year. And the printer is almost 7 years now. So far so good. Regards and cheers.

---

### Post by ajgreeny on 2022-12-04
If your cartridges have an integrated ink nozzle it could be worth simply removing the cartridge and letting it sit nozzle down on a wad of wet blotting paper or folded kitchen paper for a fairly long time, eg, 30 mins. 

I have used this method occasionally with great success but it depends on the cartridge type; if your printer has separate ink tanks it will not be possible to use this method unless you can actually remove the ink printer head itself.

---

### Post by Claus7 on 2022-12-04
Hello,

if you have access to the nozzles of the printer it would be a nice idea to use alcohol for cleaning purposes. I wouldn't like to dishearten you, yet I think that you should start thinking buying a new printer unless black and white is ok with you. Having faced the same problem, removing parts from printer, cleaning them thoroughly and putting them back, didn't solve the issue. 

Regards!

---

### Post by mIk3_08 on 2022-12-05
I prefer to use gasoline when cleaning electronic parts, devices. It will be better to soak it with gasoline and standby for an hour or so. Be sure your electronic parts soak with gasoline will be covered because you already knew how the gasoline reacts when it is exposed to open space. Regards and cheers.

---

### Post by TheFu on 2022-12-05
> **mIk3_08 said:**
> I prefer to use gasoline when cleaning electronic parts, devices. It will be better to soak it with gasoline and standby for an hour or so. Be sure your electronic parts soak with gasoline will be covered because you already knew how the gasoline reacts when it is exposed to open space. Regards and cheers.

Hopefully, there isn't any plastic or rubber in those parts.  Gasoline will destroy those. Same for kerosene, which is a better cleaning solvent, if you have it around. For metal parts, either works well, but both will "melt" plastic.

---

### Post by ulissipus on 2022-12-05
Thanks for all the suggestion. I am down with covid right now, no way I can think of doing anything with the printer.
Or doing anything full stop...

---

### Post by oldfred on 2022-12-05
I used a q-tip & alcohol to clean dried cartridges.
That worked for me and was relatively easy.

---

### Post by ulissipus on 2022-12-12
Problem solved. Used escputil -c ten times, in three blocks, with an interval of some three hous between them. 

Printer now working perfectly.

---

### Post by TheFu on 2022-12-12
Thanks for posting the solution that worked.

Can you help the community by using the "Thread Tools" button and marking this thread as "SOLVED"?  That helps people seeking good answers like this to find them easier.

---

