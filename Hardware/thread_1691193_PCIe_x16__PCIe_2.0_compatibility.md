---
title: "PCIe x16 / PCIe 2.0 compatibility"
date: 2011-02-19
forum: Hardware
---

### Post by tbear2500 on 2011-02-19
This is not really a Ubuntu question, but a graphics hardware in general question, and I thought someone here was bound to know the answer.  I have an HP a6110n computer, which has an nVidia GeForce 6150se nForce 430 graphics card.  I've been looking to upgrade it for some time and have found that the computer has an ASUSTek narra2 motherboard, which has one PCIe x16, one PCIe x1, and two PCI slots.  I'm looking to put in a PCIe 2.0 card like an nVidia GeForce GT 440 or GeForce GTS 450 (recently I've decided to hugely widen my search, but I've been looking at one of  [_[COLOR="Blue"]these[/COLOR]_]("http://us.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=136&prod_no=2102")).  I have read that PCIe 2.0 stuff is generally backward compatible with PCIe 1.x, but I'm not sure if it would work with my system since there is no indication of 1.x.  Does the lack of indication indicate that it is 1.0?  In short, does anyone here know if I can use a card like this or not?

---

### Post by cascade9 on 2011-02-20
Narra2 is just a name used by HP. The asus model number is M2N68-LA..but there are at least 4 variants on that name (stupid asus/HP). :( 

A PCIe 2.0 video card should work in that system. 

GT440? No, dont. There are no linux drivers for that card (yet anyway). GT450? Well, there are drivers for it, but you would need to add a PPA or manually install the drivers to get them going with ubuntu. 

What is your intended use? If its gaming, spend a bit more and get a GTX460. If its for normal desktop use, GT210/220 or GT430. If its for a myth box, GT430.

---

### Post by tbear2500 on 2011-02-20
I dual boot Ubuntu 10.04 (I don't think I've upgraded yet, but I'm nowhere near the computer now) and TinyXP, which I use mostly for gaming. I was all but sure any of the cards would work, but I've realized now that my PSU has to be upgraded to supply any of them, to one with about twice the power rating of the one in my system.

As for choosing a card, I'll have a look at your recommendations, but my biggest problem is that I'm 16 and I don't own the computer (technically it's my mother's but she doesn't know how to use it anymore, so it's as good as mine). I don't have tons of money to spend on this, and she certainly isn't willing to spend much (she's one of those people who can't be convinced of the value in anything but a car if it's more than $100), which requires budget restriction. Gaming (I do MS Flight Sims and some racing sims primarily) on the 6150 hasn't quite sucked, but either minimizing graphics settings or living with <10fps has gotten old (if you want to know specifically, I specifically use mostly FSX/FS2004, rFactor, and Live for Speed, if that helps you making a recommendation).

I haven't considered Linux drivers yet thigh, thanks for that insight.

---

### Post by cascade9 on 2011-02-21
Hmm...I can see your problem. 

If is for gaming, virtually anything in PCIe would be better than the 6150se. Even a  lowly nvidia 6200 would be better (dont get one). 

You might be able to find a nice cheap 2nd hand card- I've seen 8800GTs and 9800GTs go for under $50 2d hand. 

If you dotn have access to cheap 2nd hand parts, and want to stay under $100 probably a GT220 would be the best choice as far as nvidia goes. Its not really a 'gamers' card but compared to the 6150, it would be blazing fast. They go for about $50-80

I havent checked prices on ATI/AMD cards, IIRC they are slightly faster for your $$$.

---

### Post by tbear2500 on 2011-02-21
Well I do have some (however limited) income and if I can put some money toward it (about half the cost) I should be able to get a Galaxy GTX 460 from Newegg.  I know roughly what kind of power supply I'd need and I cracked open my case to measure it today and it appears as though the card should fit; the layout of this thing really isn't great for accomodating such a card though.  I've attached some pictures to make sure I know what I'm looking at.

[IMG]http://tbear2500.x10hosting.com/images/comp/PCIs_sm.jpg[/IMG]
1: PCIe x16?
2: PCIe?
3: PCI used by network card? (it connects to the ethernet thing in the back panel, so I know it's a network card)
4: PCI?

[IMG]http://tbear2500.x10hosting.com/images/comp/measure_sm.jpg[/IMG]
I've got a good 6 inches before I start running into (albeit movable) cableage

[IMG]http://tbear2500.x10hosting.com/images/comp/Ymeasure_sm.JPG[/IMG]
I can fit a card of about an inch and a half height

[IMG]http://tbear2500.x10hosting.com/images/comp/nVs_guess_sm.JPG[/IMG]
nVidia says the GTX460 is about 8 1/4 inches long.  The card I looked at on Newegg appeared (via scaling) to look like it was no more than 6 inches.  Who do I trust?

I know I've turned this into more than a compatibility issue, but any help with this matter is still greatly appreciated.

---

### Post by cascade9 on 2011-02-22
From top to bottom. 

1- PCIe x16
2- PCIe x1 
3 + 4 PCI. 

I cant be sure its a network card from the pics. You migth be able to move it to the bottom PCI slot as well to get a bit more clearance and room for ariflow. 

I'd call it more like 7'', and the cables should be moveable. I'd proably zip-tie the USB cabling to the vents at the bottom of the case, and zip-tie the excess power cabling to..er...looks like a HDD cage to me to get everything out of the way. 

Video cards 'height' is actually in the up'down axis on yoru pic. What you cre callign 'height' is the width. Most GTX460s are 'dual slot' cards, meaning that installing one will block the PCIe x1 port. 

I'm yet to see a GTX460 shorter than 8.25'' (BTW, I find imperial measurements with a decimal point highly amusing, technically it should be 8 1/4'')

The easy way to get a rough idea of how long the card is by seeing how much overhangs behind the PCIe slot. The end on the PCIe x16 slot is always 5'' (+ tiny bit).   

I'd be careful to check the power supply rails as well (not just the wattage). GTX460s suck a fair bit more power from the 12v rail, if you have a small 12v rail you might need to get a new power suply, even if its got more than enough wattage.

---

### Post by tbear2500 on 2011-02-24
I just got clearance to buy the card!!  I'll do that now and see what I need in a power supply.  If you'd like, I'll let you know how it goes.  Thanks for the suggestions!

---

### Post by cascade9 on 2011-02-25
No problems, enjoy your new card...you will be shocked at how much faster it is. 

I'd bet you are using full AA and AF at max resolution on the same games that were chugging before the upgrade ;)

---

