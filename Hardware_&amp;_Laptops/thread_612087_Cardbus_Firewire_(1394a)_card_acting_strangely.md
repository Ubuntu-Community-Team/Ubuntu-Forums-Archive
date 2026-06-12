---
title: "Cardbus Firewire (1394a) card acting strangely"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by john8520 on 2007-11-13
Ok, so I just bought a generic Firewire Cardbus card off ebay for $8 shipped, with the intention of using it with Ubuntu (gusty 7.10) and my external hard drives and CD burners. It finally arrived today, and so right away I popped it in laptop, and Ubuntu froze. Total lockup, no mouse, no keyboard, no audio, no video updating, nothing. I feared that it had kernel panicked and I'd have to force reboot. But very oddly, when I removed the card from the slot, it all restored! My music came back on and everything went back to normal!

I find this to be very odd. I have two other cardbus cards, one USB2 and one compact flash adapter, and both work fine and are hotplug, but this one is apparently not. I had figured that all cardbus cards were hotplug in Ubuntu, and that surely a firewire card would work.

I have not yet tried booting with the card inserted, but I will do that in a moment. I will also try the card in another laptop, running Windows XPp. In the mean time, any ideas on what might be happening? The first thing that I thought was maybe it needs some driver or something.

John

---

### Post by john8520 on 2007-11-13
Ahhhhhhhh crap.

I just tried it in my other laptop with windows, and got nothing. No little bubble popping up informing me that I have inserted a firewire card, no little "new device found!" noises, nothing new in the device manager. Nothing at all. 

I think this ebay sellers has just earned himself one negative feedback...

---

### Post by john8520 on 2007-11-13
Another update:

I just remebered to check dmesg, and this is what I got:

```

[ 1000.716000] pccard: CardBus card inserted into slot 1
[ 1004.408000] PCI: device 0000:07:00.0 has unknown header type 7f, ignoring.
[ 1004.408000] pccard: card ejected from slot 1

```

So quite clearly the card is not working properly. I just checked the eBay page again and the guy does returns, so I guess all hope is not lost.

*sigh* :(

---

