---
title: "Is it possible to test the power supply?"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by Bob Morane on 2008-02-11
See the title ):P

I have some really weird and inconsistent WiFi issues, both in Ubuntu and Windows, so it's not likely to be a software issue.
Actually, the WiFi might work like a charm for hours, then after i reboot and change OS, it won't work. Or it worked one day, and the day after it doesn't.
Someone suggested it might be a power supply issue, WiFi cards being very sensitive to small voltage variations. This computer is 4 years old and never had any piece replaced. Only the WiFi card is new (1 week old)

Before replacing the power supply unit (which is something i never made by myself), i would like to be sure it's causing the issues. So is there a way to test it. Some sensors to display informations for instance.

I already made a search on the board, but the only advice i read were either trying a new one, or "licking" the PSU ](*,)

---

### Post by swazidoughman on 2008-02-11
It might be a defective WI-FI card, get a replacement
there are tools for testing a psu, but it will cost you.

---

### Post by em3raldxiii on 2008-02-11
Hi Bob,

While I am not sure of any difinitive way to test the stability of a powersupply, there are applications out there that report the BIOS voltage variances.  Alternatively, you can just boot into your bios and look at some of the voltages.  This, of course, will depend on the motherboard and the bios that it has built in.

Alternatively, you can just post the brand name and wattage of your powersupply and some hardware junkies like me will be able to give you a best guess as to whether it's *likely* that the problem is powersupply related.

For example, if you have an Enermax or an Antec powersupply, it is substantially less likely to be the culprit than something like a Sunny.

Also you might consider looking at the state of the capacitors on the board.  It's relatively common for boards of that age to have a couple of "popped" capacitors.  I highly recommend this website [http://www.badcaps.net](http://www.badcaps.net) to learn a bit more about that.  The thing about blown capacitors is that often your computer will continue to run *okay* with one or two, but may have unpredictable problems such as those you described.  More commonly, though, you would see random reboots ... but that's not an exclusive result of blown capacitors.

It is possible to change the capacitors *very* easily.  (I do it all the time).  Take a look at that website and then look over your board to see if it's the problem.

Good luck!  Post your PSU brand name and wattage and some of us will give your our opinions :D

---

### Post by rbo83 on 2008-02-11
There is a gnome applet that displays sensors and voltage and other things. Check this link :

[http://sourceforge.net/projects/sensors-applet/](http://sourceforge.net/projects/sensors-applet/)

---

### Post by swazidoughman on 2008-02-11
like i said, it may just be a defective Wi-FI card, so the best thing to do is to
replace your Wi-Fi card before you start going around licking power supplies:KS
another thing to check is if you have a good connection, because as you probably know
Wi-Fi is wireless & it could vary on responsiveness depending on where you are
It could also be that you got your Wi-Fi card from a bad company & its just the bad/cheap manufacturing process that it was made with.

& if you need to replace you PSU then you wont have to worry much, because their easy to replace

---

### Post by Bob Morane on 2008-02-11
OK, sorry for not telling this in the first post. I bought 2 WiFi cards at the same time, one for the old computer and one for a new one. Of course, the first think i tryed when i started suspecting hardware issues was inverting the cards on both computers. The new one is still working, the old one still has troubles. The cards are D-Link G510 (rev C2 with Ralink RT61 chip)

The computer is just one wall away from the router. According to iwlist -san i had a network quality between 75 and 80% today. But was unable to get a network working.

My motherboard is a Gigabyte K8NS
The PSU is a Q-TEC ATX-350 (350 W)

The Bios states
VCore OK
DDR25V OK
+3.3 V OK
+12V OK
System FAN is at 0 RPM thought, i guess it's the FAN assossiated with the PSU. CPU Fan is at 3245 RPM.

---

### Post by Whiffle on 2008-02-11
A power supply would cause other issues as well (usually hard lockups), so I don't think its a power supply issue.   IF you're willing to take it out though, most computer stores test them.

Any other weird issues?

---

### Post by Bob Morane on 2008-02-11
Some freezes sometimes, but most of them i can recover by passing the kernel reboot sequence, so it's not really hard lockups. Sometimes i just have to press the reset button, but not often. Most of the issues i had, i suspected a GC issue.

Mhh, i had a look at the sensors applet, is there a way to get the info directly from command line, and ideally to log them to a file?

The person who told me it might be a PSU issue had trouble with a D-Link card too, and they disappeared after he changed the PSU.

---

### Post by oldsoundguy on 2008-02-11
or the problem with the wireless could be the card itself and your driver set up.  
D-Link Atheros chips work better (much .. I have 3 520's on line right now)
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547) it about the chipset you have on your card.

---

### Post by Bob Morane on 2008-02-12
If it was an Ubuntu driver issue, the card would work under Windows. I have troubles in both Ubuntu and Windows.

---

### Post by oldsoundguy on 2008-02-12
then it could very well be a power supply issue.  Have you noted any other "unusual" behavior symptoms?  As I noted, they can be subtle such as freezing up or the mouse "jumping" or a lag and speed up of keyboard entries or some program that just does not load correctly.  Or the need to re-boot to "straighten things out".
It has been pointed out already that even a GOOD power supply for most usages can be purchased for well under $100  USD retail and substantially cheaper on eBay. (I got several of my Enermax units there for about 1/2 of retail INCLUDING shipping.)
And RAID arrays SUCK UP power.  Something to consider if you intend to go that route.

---

### Post by em3raldxiii on 2008-02-13
Good advice from OldSoundGuy :D

And replacing a powersupply is relatively simple.  Pull out a smattering of plugs, undo four screws (usually), and then replace with new PSU.  If your system is a few years old, then most likely you will have a 20 pin motherboard power connector - so to be safe, maybe try to pick one that has a 20/24pin connector (it has an extra 4 for modern mobos on a separate adapter thingie).  Go with Enermax or Antec (there are others that are good, but those are sorta rock-steady standards).  And yep, grabbing one from Ebay isn't a bad idea.  Alternatively, you can check places such as [www.ncix.com](www.ncix.com) or newegg or tigerdirect and see if they have sales ... sometimes as good as 50% and free shipping.

And don't forget to check your capacitors. :D

---

