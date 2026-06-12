---
title: "Asus wl107G wireless nic, should work, but does not :("
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by greatshape on 2006-01-01
hi,

I bought a Asus WL107G wireless nic because it has a Ralink RT2500 chipset, which has a native linux driver.
My laptop is a HP pavilion ze4600
I did a fresh kubuntu breezy install with the nic placed.
The nic is recognized, as i see it under the network settings in kcontrol.
The RT2500 module is loaded as well.
Though, i can't activate the nic. When i try to, it activates for about 2 seconds and then goes disabled again. I tried many things, dhcp, static, cabled nic activated/de-activated,...it won't come up like it should.

Anyone who can help me out here?

Regards, steve

---

### Post by greatshape on 2006-01-01
ok, problem solved..
Installed the RT2500 cvs drivers and everything ok now

regards, steve

---

### Post by greatshape on 2006-01-01
[QUOTE=greatshape]ok, problem solved..
Installed the RT2500 cvs drivers and everything ok now

regards, steve[/QUOTE]

Damn, not solved!
The laptop freezes many times with that card :( 
But i got it under windows(laptop=dual boot) too with that card.

Any suggestions?
Steve

---

### Post by Triad on 2006-04-24
Bump.
I have the same problem, it seems to work but it doesn't.
the module has been loaded but it can get an ip address.

---

### Post by Bigglez on 2006-04-29
Ah bugger - I was about to order one of these cards.It was recommended on FSF for crying out loud! 
[https://www.fsf.org/resources/hw/net/wireless/cards.html#FSF](https://www.fsf.org/resources/hw/net/wireless/cards.html#FSF)

So, now what?  Damn the pcmcia wifi driver conundrum. Bloody Hell!

---

### Post by GeneralZod on 2006-04-29
This should really be in Hardware; I'll ask a mod to move it.

In the meantime, if you are using a CVS build, the developers would be very happy to receive your bug reports - please *do* follow the instructions in the [README BEFORE POSTING](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=177) thread, *especially* the parts about providing debugging info before you post, though ;)

[http://rt2x00.serialmonkey.com/phpBB2/index.php](http://rt2x00.serialmonkey.com/phpBB2/index.php)

---

