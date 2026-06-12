---
title: "Ubuntu says HDD may be failing"
date: 2010-03-18
forum: Hardware
---

### Post by jfcp on 2010-03-18
On boot-up in Ubuntu only-not in Vista- I get a little window with a  message "a hard drive may be failing". Clicking on the HD icon, then  "more information", I get the "SMART Data" window. Then, looking in the  "Attributes" window at the bottom, all the entries are blue, except  number 5, which is in red, says "Reallocated sector count, Warning, value:  78 sectors.
In the upper part of the SMART window, the "self  assessment" line says"passed"; the "Overall Assessment" line says "Disk  has many bad sectors; backup all data and replace the disk". 
I've  checked this a few times now, and the 78 number is not increasing, yet  at least.
MY QUESTION IS: Should I replace the HD, monitor the  situation, or not worry about it?
I've seen other posts where a new machine gets the"many bad sectors" warning from Ubuntu,  it seems not unlikely that it's the HDD diagostic, and not the HDD that has the problem. 
Before I run out and replace the HDD, I'd like to cross-check the results with a GOOD HDD diagnostic utility(SUGGESTIONS?), from my VISTA partition, I suppose. The ones I've tried so far aren't as good as the Palimpsest utility in Ubuntu, so I haven't made any progress that route.

This is a Toshiba Satellite L355D  laptop, 200Gb HD ATA MK2035GSS, firmware version DK020M

---

### Post by andrewc6l on 2010-03-19
If the number is staying steady, I wouldn't be terribly concerned. SMART drives automatically remap bad sectors to another spot on the disk. When a disk goes bad, it will often find a lot of bad sectors and keep trying to remap them.

Here's a bit more info:
[http://www.ariolic.com/activesmart/smart-attributes/reallocated-sectors-count.html](http://www.ariolic.com/activesmart/smart-attributes/reallocated-sectors-count.html)

(And of course, continue to do regular backups :-) )

---

### Post by jfcp on 2010-03-20
thanks!

---

