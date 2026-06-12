---
title: "[SOLVED] HP PhotoSmart C6386 Wireless with Ubuntu?"
date: 2008-12-26
forum: Hardware
---

### Post by tikkyisrad on 2008-12-26
I have an acer aspire 5735-4624 laptop running intrepid.

We (as in the family) have an hp pavilion a250n that is older than the hills. Running windows xp sp3. The desktop isn't wireless so it has to have to the linksys router hardwired to it.

We kind of have a network set up. But its through the linksys software thing so I'm not positive what exactly goes on with it.

Then, as a gift for the holidays I got an hp C6386 wireless printer so that I could easily print without having to dig out all the wires from the desktop to print.

However. I can't get my laptop to recognize any wireless printers. The printer was configured as a completely wireless printer. (Partially because I forgot to buy the USB port, but also because I didn't want to deal with the whole windows thing.)

For about two whole seconds my laptop recognized the wireless printer through the icon in the top right corner. then. it was gone. (in the blink of an eye.) now i can't get it to see it again.

I went to the desktop to see if the wireless network thing noticed it. And yes, it works fine. It has all the info on it and everything. It even scanned something for me.

So. It works with windows.


My question is. How can I get it to work with my laptop?

---

### Post by pytheas22 on 2008-12-26
Did you go to System>Administration>Printing, click 'New' and let it try to find the printer?  If it didn't auto-detect it (usually it would as long as it's on the same subnet), did you try specifying the address manually?

If that doesn't work, try running the installer for [hplip]("http://hplipopensource.com/hplip-web/gethplip.html").  You may have better luck finding the printer that way.

HP is very good about Linux printer support, so you should definitely be able to get this working.

---

### Post by tikkyisrad on 2008-12-27
Thank you so much! Haha. I'm just a newbie and just put in the wrong IP without realizing that the printer has it's own separate one.

---

