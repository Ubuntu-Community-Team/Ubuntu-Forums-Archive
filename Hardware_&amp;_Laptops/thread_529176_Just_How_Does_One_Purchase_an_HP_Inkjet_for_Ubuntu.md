---
title: "Just How Does One Purchase an HP Inkjet for Ubuntu?"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by SuperMike on 2007-08-18
After being burned by purchasing the new, cheap Lexmark Z1300 inkjet, and having to take it back because Feisty won't talk with it, I'm curious as to just how one purchases a cheap HP inkjet-style printer for Ubuntu?

I mean, I have a compatibility list, but none of the printers that Wal*Mart, Target, BestBuy, or CircuitCity have match up with that compatibility list in the < $80 price range. For instance, there's an HP Deskjet 2330, but the compatibility list only has Deskjet 2300. Probably won't work, right?

I want to be an advocate for Linux and Ubuntu, but it's hard for me to persuade others to join on board when I have to tell them they have to purchase printers off of eBay (and have no return policy) in order to get something that works with Linux.

I propose that at the next Linux Hardware conference that they come up with some kind of easier way for manufacturers to make Linux-compatible drivers and especially for the low cost printers. I thought that's what Postscript was all about, but I guess there's a license on that which makes printers too expensive, so manufacturers are ditching that and using cheaper drivers.

Take for instance LaCie. They're making a Lightscribe CD disc drive and they support Suse and Ubuntu/Debian. It not only will read/write to it with a driver they made at LaCie, but they provide software that can draw Lightscribe images on top the CDs. Why can't HP and Lexmark get with the program and realize that it's worth their time to work with us?

And if that can't work, then perhaps there's some sort of kludge that one can install on Linux that lets you use the Windows drivers for your printers. It may go down the non-free, proprietary route, which of course I don't like, but I need to get something accomplished.

---

### Post by verbalshadow on 2007-08-18
In my experince you  have a really good shot at that printer working. I have HP PSC-1315 and it wasn't listed in the compatiablity list.
But it worked fine with the PSC-1310 driver auto detected and everything. I can't promise it will work, but it worked for me.

Not sure but is this the printer you are talking about i didn't see a deskjest 2230 [http://www.openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_2230](http://www.openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_2230)  if so that it should work.

HP is one the best for having drivers for there printers in linux. They have released code and programs besides for compatiablity.
Lexmark not so much.

Hope it works for you.

---

### Post by DiamondX on 2007-08-19
Im 95% sure that the second 2 numbers dont matter, so if it says 2300 works, it actually means 23xx works. This is because the models are so similar that the same drivers works equally well for both.

---

### Post by ericesque on 2007-08-19
I recommend going to Best Buy and asking one of their sales associates.  I'm sure they will be more than helpful....  bwuuuuuaaaa-hahahahahaha!

:lolflag:

---

### Post by pbcartwright on 2007-08-19
like the other person said, they work fine. I have an all-in-one 5620, but the driver says 5600.. just install these drivers:

hplip-hpijs-2.7.6-1.pm.1
hplip-2.7.6-1.pm.1

---

### Post by Sef on 2007-08-19
> Why can't HP and Lexmark get with the program and realize that it's worth their time to work with us?

Most [HP]("http://openprinting.org/printer_list.cgi?make=HP")s will work on GNU/Linux; Most [Lexmarks]("http://openprinting.org/printer_list.cgi?make=Lexmark") will not.

---

### Post by SuperMike on 2007-08-19
Okay, gang, my wife and I went to Office Depot and picked up a brand new HP Deskjet 6940 for $119, and then got a cartridge pack (black and color, extra) for $58. 

Ubuntu 7.04 (Feisty) found the printer right away, selected the proper driver, and used hpijs (as recommended on the web) by default. It works fantastic and fast, including right/left/center alignment, super and subscript, bolding, italics, colors, etc. I noticed that it can spit out a color photo from Firefox super fast as well -- faster than I imagined it should take. When you print, it takes about 5 seconds and you receive a color image (5 in x 5 in was what I chose).

We returned the Lexmark Z1300 printer and got our money back. The lady at Wal*Mart didn't even look inside the box. They wouldn't, however, take opened cartridges back.

The guy in Office Depot asked what operating system we were going to use it with, and I said Ubuntu Linux. A big smile came across his face and he said, "Really? I use Fedora Core at home." I think he was thrilled that at least I was a Linux fan like he was.

Sure, my printer selection was rather limited, but at least I could get a new color printer without issues and the driver is free. I didn't see any cheaper color printers that were supported by Ubuntu 7.04 at Wal*Mart or Office Depot -- not on their website, and not in the stores. So, I recommend you snatch up the HP Deskjet 6940's while you still can. We purchased the last one at Office Depot in town.

And to whomever wrote us all this free printer driver -- you've made my family happy today.

---

### Post by SuperMike on 2007-08-20
We found that Abiword won't let us print on the 6940 as far as photos. The job sits in the Q and remains there. We saved as a DOC file and then reopened in OpenOffice (after we added the OO speed hacks, of course!). It looked the same. We were able to print just fine to the 6940 through OO.

---

