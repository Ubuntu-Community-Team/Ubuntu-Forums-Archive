---
title: "A-LINK WL11PC doesn't work"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by teerik on 2005-08-25
I have HP Compaq NX9010 laptop with Ubuntu Hoary. I've installed latest rt2400 cvs drivers successfully, AFAIK. No errors and..

$ lsmod |grep rt2400
rt2400                 67264  0

So it looks good for now. But then I face problems when trying to get the PCMCIA card up:

$ ifconfig ra0 up
ra0: ERROR while getting interface flags: No such device

Then I found out that the machine sees the card but it isn't recognized correctly. Or am I right?

$ cardctl status
Socket 0:
  3.3V CardBus card
  function 0: [ready]

$ cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

Could someone please give a hand for me? What should I try? I've googled pretty much with no help.

---

### Post by teerik on 2005-08-29
Nobody really can't help? I'm pretty puzzled with this. Is there some hardware incompatibility or have I just forgot to do something.. like some PCMCIA settings. I'm total newbie with laptops and PCMCIA cards. Is that "cardctl info" output normal? It doesn't look like it.

---

