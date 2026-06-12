---
title: "HAL failed to activate PCMCIA slot after hibernation"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by heiko.nolen on 2007-05-13
Note: I'm still pretty much a newbie with Linux so i might not get everything right in my description of the problem, but will try my best... :)

As of right now, my wireless card (which used to work flawlessly) has stopped even giving the green light for power. My theory is that HAL failed to reactivate the PCMCIA slot after a hibernation, and I just can't figure out how to reactivate it manually.

I've tried ejecting and inserting (both physically and using cardctl / lspci), but the only report I get is: "no card".

My feeling is that if I could run a line to set the power status of the PCMCIA slot to whatever state means active, then all I'd need to do is to plug in the card manually...

Help?

---

### Post by heiko.nolen on 2007-05-13
So I dug a little further on my own and learned about this thing called cardmgr. I entered:

sudo cardmgr

and got the following error messages:

cardmgr[12875]: could not adjust resource: IO ports 0x100-0x3af: Function not implemented
cardmgr[12875]: could not adjust resource: IO ports 0x3e0-0x4ff: Function not implemented
cardmgr[12875]: could not adjust resource: IO ports 0x820-0x8ff: Function not implemented
cardmgr[12875]: could not adjust resource: IO ports 0xc00-0xcf7: Function not implemented
cardmgr[12875]: could not adjust resource: memory 0xc0000-0xfffff: Function not implemented
cardmgr[12875]: could not adjust resource: memory 0xa0000000-0xa0ffffff: Function not implemented
cardmgr[12875]: could not adjust resource: memory 0x60000000-0x60ffffff: Function not implemented
cardmgr[12875]: could not adjust resource: IO ports 0xa00-0xaff: Function not implemented

Am I even on the right track?

---

