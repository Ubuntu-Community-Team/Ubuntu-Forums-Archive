---
title: "Best hardware setup to fax and make phone calls in Ubuntu? ATA + Asterisk?"
date: 2009-08-20
forum: Hardware
---

### Post by Gustavo Narea on 2009-08-20
Hello, everyone.

I'll have a server at the office of a small organization, which we'd like to use (among other things) as a *VoIP Gateway*. This is, we'd like to send and receive faxes from the computers in the local network, as well as make and receive regular/analog phone calls from the computers in the network. The software part is already decided (we'd use [Asterisk]("http://www.asterisk.org/support/about")), but it's not clear to me what would be a good hardware setup for this under Ubuntu -- I hope somebody with experience in this can help me out.

I've discarded fax-modems because they are usually a nightmare in Linux and also because it wouldn't work with software such as Asterisk.

After some research on the Web, it seems like the only solution is using an ATA ([Analog Telephone Adapter]("http://en.wikipedia.org/wiki/Analog_Telephony_Adapter")), to bridge the Plain Old Telephone Service and our LAN. However, I've read lots of things about ATAs and I'm still confused about some things in the way it works and its support in Linux (specially Ubuntu):

[LIST]
[*]Most ATAs use an Ethernet interface. Is it connected to a computer or a router? It could sound like a stupid question, but it all comes down to this: How does it work? Like a server connected to a LAN in which clients must connect to it via some ports? Like a modem?
[*]Others use an USB connection (so here it's a sort of modem). Then what's the best supported method in Ubuntu, the Ethernet or the USB one?
[*]What brand (and possibly model) of ATA are well supported in Linux?
[*]Are ATAs the best solution anyway?
[/LIST]

I know Asterisk works with ATAs, but I'm concerned about how well it works under Ubuntu this way.

If you know something better than an ATA, please let me know. :)

Thanks in advance!

---

### Post by Gustavo Narea on 2009-08-24
Anyone? At least any pointer to get the answer to my questions?

---

### Post by afrodeity on 2010-08-09
Also wondering what the answer is. I just installed a HFS modem so that I can fax and get incoming caller id.

---

