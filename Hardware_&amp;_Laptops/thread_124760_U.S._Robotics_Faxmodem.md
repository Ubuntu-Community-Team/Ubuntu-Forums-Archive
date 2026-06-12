---
title: "U.S. Robotics Faxmodem"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by jason.b.c on 2006-02-02
Hello ,Does anyone know if i can get a u.s.r (model #5699b) pci modem working under breezy 5.10,  I've been searching the forums left and right but have'nt found really anything that helps much. I'm not sure on what chip it has or what the part(model) number it has ( It's sorta currently installed my computer that i'm using to type all this ):rolleyes: 


56.K Faxmodem PCI for Windows   
     U.S.R.5699b
 SN:  2MBHY4BF3053
  V.92 and V.90 itu standard

---

### Post by jason.b.c on 2006-02-02
:mad: ok so i googled for u.s.r modem drivers in ubuntu , and i found the following sites and still really no help ..:mad: 
 
   Linmodems.org
  Serial.sourceforge.net
  modem-drivers.net
  usr.com/support

does anyone have any ideas on where else i can search:) or am i just  S.O.L. ON THIS ONE?      
                       also while were at it does anybody know of any ( external modems ) that are known to work in breezy?? that might be the only way i can go on this one THANKS!:(

---

### Post by az on 2006-02-02
US robotics are notorious for not supporting linux.  Their hardware modems are great, but they stick it to linux users with ther software modems.

---

### Post by Bartender on 2006-02-02
Hi, Jason - 
check here

[http://start.at/modem](http://start.at/modem)

The lists are a little hard to read at first.  Look for the legend, describing what the various icons in the lists mean.  Near there you'll see buttons to click that'll take you to lists for PCI, serial, etc.  USR is listed twice in these lists, under "3Com/USR" and again as "US Robotics Access. Corp"

In the PCI list under "3Com/USR" I found listings for the 5699.  Didn't see a separate listing for the -B but coulda missed it.  Unfortunately, that big red "W" to the left indicates it's a Winmodem.  That doesn't mean you can't make it happen, it just means it ain't gonna be Plug N Play if you know what I mean.

I'm looking for a coupla externals because it's unlikely I'd be able to do the tweaking that's described in the forums to make winmodems work.  If you feel you may be in the same boat take a look at the "Serial" list on this same website and you'll see a lot more modems with the good icons.  US Robotics is a good brand to hunt for but as you'll see there are others.  Notice that ancient 28.8k modems are listed right along with 56K V92's.  So read thru there carefully, make yourself a list, then go shopping.  There's a truckload of externals coming up on Ebay.  Hopefully we won't get into a bidding war...

---

### Post by Hygelac on 2006-02-02
I once had to try getting one of those modems to run in Ubuntu, but found it to be impossible. As far as I know (though be warned that I'm a noob) USR modems don't work under Linux.

EDIT: Then again, have you tried installing and running 'scanmodem' to see what it says?  I had never done that, so maybe it's worth it.

---

### Post by jason.b.c on 2006-02-02
:) :) Hey thanks guys for your quick response's i'll surely give that web site that bartender suggested a thorough lookin' over!   :cool:  I'm currently tabbed on another site ( linuxselfhelp.com ) right now but bartenders site is my next stop :cool: anymore suggestions would be helpful ,thanks....:)

---

### Post by az on 2006-02-02
USR Use a chipset that does not have any linux drivers.  A lof of winmodems work in linux, like lucent, intel, pctel, (conexant - with drivers you have to buy)  Some can even work using alsa, if they use the ac97 codec.

USR sometimes use the conexant chipset, but usually use their own, which will not work in linux.


I would love to be wrong about this.

---

### Post by az on 2006-02-02
[http://freewebhosting.hostdepartment.com/g/gromitkc/analog/ad1807_1804.html](http://freewebhosting.hostdepartment.com/g/gromitkc/analog/ad1807_1804.html)

Chipset data:
Manufacturer 
Analog Devices, Inc., a custom chipset for 3Com, based on the ADSP-2189. 
Datasheet not available 
Applications 
Controllerless modem, small footprint 
Identifiers 
PCI vendor ID: 12B9, PCI device ID: 1007 
Linux support 
3Com has not released a Linux driver for the AD1807/1804-based Winmodems

Components 
AD1807  Data Pump
AD1804  Silicon DAA
AD1803  Voice Codec     24-pin TSSOP (optional)
Image

---

### Post by jason.b.c on 2006-02-02
:KS :o Hey bartender/azz i think i found something 
  ( free.hostdepartment.com/g/gromitkc/conexant/conexant_rs56pci.html )
  tell me what you think?:cool:

---

### Post by az on 2006-02-02
[QUOTE=jason.b.c]:KS :o Hey bartender/azz i think i found something 
  ( free.hostdepartment.com/g/gromitkc/conexant/conexant_rs56pci.html )
  tell me what you think?:cool:[/QUOTE]

I don't think that's your modem's chipset.  What makes you think so?

---

### Post by jason.b.c on 2006-02-02
( free.hostdepartment.com/g/gromitkc/conexant/conexant_rs56pci.html )
tell me what you think?

I don't think that's your modem's chipset. What makes you think so?

:KS Oh no no , I don't mean that website for my U.S.R modem , I mean what about that modem ( I.O.W ) SWAP MODEMS ???:rolleyes: sorry that i was'nt any clearer before..

---

### Post by az on 2006-02-02
Pretty awful.

You will need to *buy* linux drivers for it for 15 bucks.  You may also find it stops working in the future, because the drivers will no longer match the kernel - you will have to buy newer drivers then, again.

Try lucent or intel.  The lucent ones only have binary-only drivers available, but at least they don't change for them.  The intel ones are the same, but may be the first ones to work with the GPL'ed (free-libre open source) alsa driver.

---

### Post by jason.b.c on 2006-02-02
OK well i guess either i'll give what you suggested a shot or who knows i might just get lucky here in the real near future :) I think actually i'd rather have an external one anyway because i've had to put three modems in my computer now in the past six months and i'm getting tired of opening this darn thing up every time that happens , besides that i saw on the internet here just about an hour ago were people have had really good luck with the external one's:confused:

---

