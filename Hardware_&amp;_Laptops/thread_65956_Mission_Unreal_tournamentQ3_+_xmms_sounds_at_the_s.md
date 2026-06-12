---
title: "Mission: Unreal tournament/Q3 + xmms sounds at the same time"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by _Pete_ on 2005-09-15
As the title says, that's the goal.

Hardware used for sound is currently:

Asus P4GE-VM built-in
SB live 24 pci card
Yamaha 724 based card (not currently in machine)

So far no luck for the goal. Using equipment listed, what is the best way to
get to the goal?

---

### Post by evilghost on 2005-09-15
The problem is your Sound Blaster Live 24bit, despite the deceptive advertising done by Creative, does not support hardware mixing.  The older and more capable Sound Blaster Live 5.1 (specifically, any card with an emu10k1 chipset) supports 32Channel hardware mixing.  Until your card can successfully hardware mix you will have issues.  Granted, there is software mixing, but I've been unable to get some applications to work correctly that directly lock /dev/dsp or /dev/adsp.

Ideally, you'll want a card that can hardware mix.  Consequently, I purchased 10 of these emu10k1 cards off Ebay and have been distributing them to fellow Ubuntu users in a simliar situation as you.

I'm only asking $10/card + shipping.  If you're game, just PM me your address and I'll ship one out.  See some of my many replies in the Ubuntu Gaming forum for more specific details.

[EDIT]:  I see you're in Finland, so I doubt I can ship there, however, see if you can dig-up or find an emu10k1 card and you'll have all your problems resolved.

---

### Post by _Pete_ on 2005-09-16
[QUOTE=evilghost]The problem is your Sound Blaster Live 24bit, despite the deceptive advertising done by Creative, does not support hardware mixing.  The older and more capable Sound Blaster Live 5.1 (specifically, any card with an emu10k1 chipset) supports 32Channel hardware mixing.  Until your card can successfully hardware mix you will have issues.  Granted, there is software mixing, but I've been unable to get some applications to work correctly that directly lock /dev/dsp or /dev/adsp.

Ideally, you'll want a card that can hardware mix.  Consequently, I purchased 10 of these emu10k1 cards off Ebay and have been distributing them to fellow Ubuntu users in a simliar situation as you.

I'm only asking $10/card + shipping.  If you're game, just PM me your address and I'll ship one out.  See some of my many replies in the Ubuntu Gaming forum for more specific details.

[EDIT]:  I see you're in Finland, so I doubt I can ship there, however, see if you can dig-up or find an emu10k1 card and you'll have all your problems resolved.[/QUOTE]

But is it somehow possible using two cards to solve this problem? I know one solution could be to put a wire from card0 output to card1 input but that sounds silly ... :)

---

