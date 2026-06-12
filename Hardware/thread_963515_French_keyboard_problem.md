---
title: "French keyboard problem"
date: 2008-10-30
forum: Hardware
---

### Post by roger_1960 on 2008-10-30
Hi

I have two french laptops with AZERTY keyboard running english ubuntu. Normally, on a french keyboard, I would expect CAPS LOCK, when set, to lock the long line of numbers at the top of the keyboard, ON (as it did on the same PC with the MS OS).  In fact it just locks on &É"'(-È_Ç instead of 123456789.  The only way to get the numbers is by pressing shift with each number.  This applies to both laptops.

I realise that I can set the CAPS LOCK key to act as SHIFTLOCK and get to the numbers this way, but if I do this, in a spreadsheet I cant tab or move across cells without selecting them all!!

I have tried to look in the french forums, but my french isnt really up to it!  Does anyone have a solution for this?

The relevant part of my Xorg.conf is:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Whoo Hoo  Found the solution today 29/10/11.  In Ocelot, system settings, keyboard, options, miscellaneous compatability options, tick both shift keys together toggle shift lock.  Finally I can use the numbers on french keyboards without having to use both hands!!

---

