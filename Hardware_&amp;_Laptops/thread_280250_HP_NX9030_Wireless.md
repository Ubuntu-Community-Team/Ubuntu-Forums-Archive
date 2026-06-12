---
title: "HP NX9030 Wireless"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by auror on 2006-10-19
Hi

I am a newby to ubuntu.

I have installed it on a HP NX9030 laptop and all went well except the wireless. It has found the wireless hardware ok but it doesn't work. The laptop has a wireless switch on the front and a blue light to indicate that it is active. The blue light will not come on when you push the button. It did work under windows, however only once windows booted and was loaded. I wondered if it needed the windows driver to activate the switch ?

Any thoughts ?

Nigel

---

### Post by jml on 2006-10-19
I had a similar problem with an HP NX6110.  First the blue light.  In windows the Blue light stays on continuosly when the card is active.  Once you get your card working in Linux, it will only flash briefly when it is transmitting or recieving data.

If your card is "found" by Ubuntu, (its listed when you go into the networking application, then start by turning off encryption at the base station.  Then go into the networking application again, select the wireless card, click on configure, fill in the blanks.  Back out and highlight the card again, click on activate the connection button  after it completes, close out the application and see if you can connect.  If that works, then you simply need to turn on encryption if you need it.  By the way, only WEP encryption is supported out of the box.  WPA encryption is a bit more complicated.  Searching this forum and the Wiki will give you a lot of information on this topic.

If you can't connect without encryption, then it may be a driver problem.  HP laptops usually use one of two chipsets.  The higher end laptops usually come with an Intel chipset.  You can get linux drivers for this card by going to the Intel web site and search for drivers.  Other HP laptops come with the Broadcom chipset, (mine did)  Ubuntu supplies a Linux driver for this chip set, but according to many posts I've read here, it does not work very well.  I have not done this, but according to posts on this web site, you need to blacklist the broadcom driver, and use NDISWRAPPER with the Windows driver supplied on the CD that came with the laptop  Theoretically that should work.  Again, searching this forum and the wiki for terms like Broadcon, will point you to the information you need.  Hope this helps.

Joe

---

### Post by auror on 2006-10-20
Joe

That worked, thanks very much.

Does the wireless button still switch it off and on ?

Nigel

---

