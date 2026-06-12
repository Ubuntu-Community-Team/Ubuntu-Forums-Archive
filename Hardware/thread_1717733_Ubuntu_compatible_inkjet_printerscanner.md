---
title: "Ubuntu compatible inkjet printer/scanner"
date: 2011-03-30
forum: Hardware
---

### Post by noteviljoe on 2011-03-30
Having searched ubuntu forums as well as googled for printer reviews I find myself thoroughly confused, so hoping users here might have some personal tips for a good all round Ubuntu compatible inkjet printer/scanner.

Currently using Ubuntu 10.4 but plan to switch to 11.04 when it comes out.
32-bit

Printer:
Inkjet (pref' with low ink cost)
Multi-function, should have scanner as well
Wireless would be nice but not that bothered.
Don't need to share over network - only one computer will use.
Not too massive (only have a small office)
Should be able to fast print medium volume in draft black, and also beable to print good quality (but doesn't matter if slow) high res' colour
Price:£100 -£200 


I was thinking about getting a HP printer as people seem to be saying that they have a good record of working out of the box with linux, however on a number of threads people seem to be saying that their build quality has recently gone down hill.

---

### Post by noteviljoe on 2011-03-30
One option that looks ok is the Canon Pixma MX870, but from this thread [http://ubuntuforums.org/showthread.php?p=10212785](http://ubuntuforums.org/showthread.php?p=10212785) is sounds like it might be a bit of a pain to get it working.

Actually their seems to be a slightly updated version Canon PIXMA MX885, anyone got any info about whether this will work on Ubuntu?

The companies page seems to suggest that there are drivers [http://software.canon-europe.com/products/0011008.asp](http://software.canon-europe.com/products/0011008.asp) but it would be great to get a personal testimony before I shell out all that dosh.

---

### Post by KegHead on 2011-03-30
Hi!

I have a Canon mp 250 that works ok..I needed to add drivers etc.

Also an HP 5610 that prints ok, have not tried scans.

KegHead

---

### Post by noteviljoe on 2011-04-20
> **KegHead said:**
> Hi!

I have a Canon mp 250 that works ok..I needed to add drivers etc.

Also an HP 5610 that prints ok, have not tried scans.

KegHead

Thanks, I've not been able to find any def' evidence that the Canon PIXMA MX885 will work on Ubuntu but given that there are linux drivers I think I might risk it and buy it.

---

### Post by magicfab on 2011-04-20
Hello, i saw your request for help on Identi.ca.

I'd suggest checking your printer compatibility at:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Generally speaking any printer marked as working Perfectly will be supported in any Gnu/Linux distribution. Double checking with Google for existing reports also helps. Try & always shop local at places where the return policy will let you return a printer if it doesn't work as expected.

My personal recommendation would be to buy HP, their management software is also free open source and their networked printer+scanner+fax+card reader devices install automatically very easily (package: hplip-gui).

Good luck and come back to share your choice.

---

### Post by magicfab on 2011-04-20
I checked Canon's site regarding the model you asked about and they provide binary, non-free drivers for Ubuntu 10.04 LTS. Although this may work, you'd be stuck when you upgrade if anything stop wrking as Canon most likely won't support other versions of Ubuntu until they get to them and there won't be much community support without having access to source code.

My personal suggestion would be to stay away from such manufacturers.

---

### Post by noteviljoe on 2011-04-21
> **magicfab said:**
> Hello, i saw your request for help on Identi.ca.

I'd suggest checking your printer compatibility at:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Generally speaking any printer marked as working Perfectly will be supported in any Gnu/Linux distribution. Double checking with Google for existing reports also helps. Try & always shop local at places where the return policy will let you return a printer if it doesn't work as expected.

My personal recommendation would be to buy HP, their management software is also free open source and their networked printer+scanner+fax+card reader devices install automatically very easily (package: hplip-gui).

Good luck and come back to share your choice.

Thanks.

Not sure how my request got onto Identi.ca. as I posted it on twitter? Does Identi.ca. sync with twitter?

I was thinking of HP but as I said above the reviews all seem to be slagging off their quality at the mo'.

I was thinking that there was a fair chance that the Cannon drivers would work in 11.04 even though only marked as for 10. Do you think that there is a fair chance that they won't?

I think your point about buying local is good, I was going to buy off internet but you are right returns is thus a pain.

---

### Post by noteviljoe on 2011-04-21
I've had a rethink, now I'm considering the HP Officejet Pro 8500A
[http://www.amazon.co.uk/Officejet-8500A-All-Enabled-Printer/dp/B003VYB70Y/ref=pd_cp_computers_1](http://www.amazon.co.uk/Officejet-8500A-All-Enabled-Printer/dp/B003VYB70Y/ref=pd_cp_computers_1)

---

### Post by walt.smith1960 on 2011-04-21
HP has a very good rep supporting the Linux community.  I'm sure their recent models aren't built to the durability standards of the old Laserjets; not many SOHO printers are these days. I've had quite good success with 2 brother MFD's, an older MFC-7820N and a MFC6490CW. The MFC6490CW is no one's idea of compact but it is an affordable Ledger/A3 printer. The software is found here:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)  You can check there that printer and scanner software are available for any machine you might be interested in.  Simply googling something like "manufacturer+linux" should take you to the manufacturer's linux software source. If the manufacturer doesn't have Linux software for the model you're interested in, that may tell you what you need to know.

Regarding ink costs, consider spending a little time on Ebay using "refillable ink"+ manufacturer as search criteria.  I have refillable cartridges for both the Brother MFC-6490CW and HP Photosmart which uses HP02 cartridges.  Both work. One fact in favor of the Brother is there is no "kill me" chip or other electronics in my Brother cartridges so it's simple to make refillable cartridges; it doesn't require an autoreset chip.   There are also retrofit continuous ink supplies listed on Ebay. I have no experience with those.

---

### Post by bazdavis on 2011-04-21
I'm using a Epsom TX800FW multifunction printer,scanner,fax and it prints double sided it is connected as a network printer although it is wifi capable I don't use this function. Once the printers functions were set after cups detected the printer it's been operating brilliantly.:)

---

### Post by Matsumoto on 2012-03-18
> **noteviljoe said:**
> Actually their seems to be a slightly updated version Canon PIXMA MX885, anyone got any info about whether this will work on Ubuntu?

The companies page seems to suggest that there are drivers [http://software.canon-europe.com/products/0011008.asp](http://software.canon-europe.com/products/0011008.asp) but it would be great to get a personal testimony before I shell out all that dosh.


Late reply - I just got the printer and got it running under Debian Testing with the drivers provided by Canon. 
And I must say, duplex is really nice :-)

For details just ask me or have a look here:
[http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html](http://blog.kenweiner.com/2011/04/using-canon-pixma-mx882-all-in-one-with.html)

---

