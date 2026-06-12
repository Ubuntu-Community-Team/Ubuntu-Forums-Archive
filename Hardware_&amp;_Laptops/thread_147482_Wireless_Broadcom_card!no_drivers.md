---
title: "Wireless Broadcom card!no drivers"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by norby on 2006-03-20
I would like to now if there is any solution to use 54gBroadCom Wireless Card since the manufacter does not provide any drivers for this equipment for unix/linux plataform? Does any one as the same problem our does any one has a diferente solution?

---

### Post by int on 2006-03-20
just perform a search here! for broadcom

---

### Post by jml on 2006-03-20
Which version of Ubuntu are you using?  There are no native Linux drivers for the Broadcom chip set.  But I'm pretty sure I've read that the next version of Ubuntu ,(aka Dapper Drake) will include some support for the Broadcom chipset.  For now, the solution is a little more complex.

You first need a program called NDISWRAPPER.  I cant recal if it is installed in Ubuntu by default, but if you open Synaptec and type in NDISWRAPPER you should be able to tell if it is installed or not.  If is is, you are already part of the way there.  If not download and install it.

Once you have it installed, the next step is to take the Windows driver that came with the card and run NDISWRAPPER. You can get the windows driver either from the install CD that came with the wireless card, or you should be able to download the most current one from the Broadcom web site.

Then its a matter of configuring your card followed by activating it.  These two steps are performed from within the network configuration application.  The steps are a bit more involved than I have listed here, but the previous poster is correct.  If you search on the terms, Broadcom, Wireless, you should be able to find very detailed postings with nearly step by step instructions.  Hope this helps.

Joe

---

### Post by bklebel on 2006-03-20
when I try and install my windows driver (bcmwl5a.inf) with ndiswrapper I get an error: **cp: cannot stat `bcmwl5a.inf': No such file or directory**

does anyone have an idea of what I may be doing wrong?

---

