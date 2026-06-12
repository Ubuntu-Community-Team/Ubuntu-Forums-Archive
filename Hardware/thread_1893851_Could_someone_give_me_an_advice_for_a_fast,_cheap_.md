---
title: "Could someone give me an advice for a fast, cheap network printer?"
date: 2011-12-11
forum: Hardware
---

### Post by Bazon on 2011-12-11
After no one seems to have an answer for [this problem](http://ubuntuforums.org/showthread.php?t=1893520), it's time to buy a new printer I suppose.

So could someone please give me an advice for a network printer working good with ubuntu which is cheap and fast? 
(I only need it for text + basic graphics, but often for many pages.)

thank you!

---

### Post by kurt18947 on 2011-12-11
I've never use a router with what I guess is a built-in USB printer server so can't help there. The printer works properly when not connected through the print server so I assume the problem is not with the printer software on the PC.   HP has an excellent reputation for Linux compatibility.  I've had good luck with 2 Brother networked  multifunction machines though HP setup seems plug & play.  One Brother machine seems to not be in the foomatic database so I have to do a manual install with it. Brother does offer Linux drivers for its machines. HP has a utility (HPLip) that allows on-screen monitoring of ink levels etc. Brother does not.  If I were considering Lexmark, Dell (rebranded Lexmark), Kodak or Canon, I would do some research about Linux driver availability before purchasing.  No sense in buying a problem.

Edit:  For your purposes, lots of text and don't need color a laser would be the way to go IMO.  Samsung lasers seem to get positive reviews. I'll also relate a problem & solution with my Brother MFC-7820N.  It was terribly slow with 2nd and subsequent pages.  The default driver was  BrScript 3.  I found on Synaptic a CUPS driver for this machine.  MUCH faster.

---

### Post by aeronutt on 2011-12-11
Looking at your other post, I'm thinking this is a router print server problem, and not a printer problem.

"...If the printer is connected to the PC directly or via a Windows computer (samba), the problem doesn't occur."

---

### Post by Bazon on 2011-12-11
> **aeronutt said:**
> Looking at your other post, I'm thinking this is a router print server problem, and not a printer problem.

"...If the printer is connected to the PC directly or via a Windows computer (samba), the problem doesn't occur."

That's why I'm interested in a genuine network printer this time, not connected by USB (as before) but by LAN or WLAN.
(There are machines like that, aren't there?)

---

### Post by Bazon on 2011-12-11
> **kurt18947 said:**
> HP has an excellent reputation for Linux compatibility.  I've had good luck with 2 Brother networked  multifunction machines though HP setup seems plug & play.  One Brother machine seems to not be in the foomatic database so I have to do a manual install with it. Brother does offer Linux drivers for its machines. HP has a utility (HPLip) that allows on-screen monitoring of ink levels etc. Brother does not.  If I were considering Lexmark, Dell (rebranded Lexmark), Kodak or Canon, I would do some research about Linux driver availability before purchasing.  No sense in buying a problem.

Edit:  For your purposes, lots of text and don't need color a laser would be the way to go IMO.  Samsung lasers seem to get positive reviews. I'll also relate a problem & solution with my Brother MFC-7820N.  It was terribly slow with 2nd and subsequent pages.  The default driver was  BrScript 3.  I found on Synaptic a CUPS driver for this machine.  MUCH faster.

Thank you, good to know. 
And because of my blank extra page problem, I prefer not to rely only on driver compatibility but actual experiences by other users.

---

### Post by aeronutt on 2011-12-11
FYI, good experience with my HP office jet J6480 via wireless.

---

### Post by agillator on 2011-12-11
Although we are tending to sound like a broken record, I would also recommend HP. That doesn't mean others are bad, it only means HP is all I have used for years. I have used them in all the modes (assuming they are built for that mode, of course). You can find them in all price ranges. The photosmart printers are definitely worth looking at. Don't let the name fool you, they do everything well and quickly and tend to be slightly less expensive. Personally I use the OfficeJet 'All In One' printers. If you are in the US, check out OfficeMax. A week ago they were having a sale. I think it is 'model change' time for HP so Office Depot, Best Buy and others may also have them on sale.

---

### Post by docbop on 2011-12-11
Network you mean a wired network???

I tend to good with HP printers since there always seems to be a driver for them somewhere.  Other printers be sure to check for a drivers before you buy.

if you look at sites that sell close-outs and refurb printers you can usually find good deals on printers with wired network support.   HP is starting to move away from wired network suport on home printers, so many of the older wired printers are available cheap.  I just recently picked up a refurb $500 HP SOHO printer for $100.   works great and all my computers had drivers for it.

---

### Post by Bazon on 2011-12-11
> **docbop said:**
> Network you mean a wired network???

I don't understand the difference.

Thanks for your recommendations @ all! :-)
So I think it's gonna be a HP...

---

### Post by kurt18947 on 2011-12-11
> **Bazon said:**
> I don't understand the difference.

Thanks for your recommendations @ all! :-)
So I think it's gonna be a HP...

Networked printers can be connected to a router via ethernet cable or via wireless networking.  Wireless networking is certainly convenient, you don't need to have the device close to the router or a network jack.  On the other hand wired may have less security issues.  There was a recent thread on this forum about ways an attacker could use a networked printer to penetrate a LAN.

Edit:  Here's the security related post  [http://ubuntuforums.org/showthread.php?t=1876828](http://ubuntuforums.org/showthread.php?t=1876828)

---

### Post by Bazon on 2011-12-30
When I speak about "network", I mean wired network.
When I mean wireless network, I say "WLAN".

So much for individual language use. ;-)

Finally, I got a Samsung ML-2525W which works very fine as a *(wired)* network printer. :-)
*(It has WLAN, too, but I don't use it. I like wires.)*

---

