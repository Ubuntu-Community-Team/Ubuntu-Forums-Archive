---
title: "Help with TV Tuner"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by zhinker on 2007-04-21
I've got AverMedia's UltraTV 1500 MCE video card.  Could someone please tell me what program I should use to make it work on Ubuntu 6.10?


Thanks

---

### Post by kevinatkins on 2007-04-21
Hi,

TVTime is a very good television viewing application - you get really nice picture quality. I'd hesitate to recommend the Gnome TV application 'Zapping' - from my experience it's far too crash-prone, although YMMV.

---

### Post by zhinker on 2007-04-21
hmm...I went to it's website to see if my card was compatible but it named the type of cards that were supported instead of actually stating the names/brands of the cards.  I guess I'll just have to try and see, Thanks

---

### Post by zhinker on 2007-04-21
> **kevinatkins said:**
> Hi,

TVTime is a very good television viewing application - you get really nice picture quality. I'd hesitate to recommend the Gnome TV application 'Zapping' - from my experience it's far too crash-prone, although YMMV.

Nope, neither of them worked.  When I tried to use TVTime it would just open up for a split second and then close again.  And when I tried Zapping I would get an error saying:

[INDENT]Couldn't open /dev/video0, try other devices?[/INDENT]

and when I said yes I'd see the error
[INDENT]
Sorry, but "/dev/video0" could not be opened:
The device cannot be attached to any controller[/INDENT]

Any ideas on how to fix that?

---

### Post by kevinatkins on 2007-04-22
Hi,

Hmm - I think I see your problem now... the UltraTV 1500 being a hardware accelerated card. I've had a bit of a scour of the internet and I can't find any driver, so you might be out of luck. If you can identify the chipset on the card, then it's just possible that you might be able to turn up some more information. Sorry I can't be of more help here.

---

### Post by zhinker on 2007-04-22
How do I find out what the chipset is?

---

### Post by Erlander on 2007-04-23
In terminal enter dmesg

Rob

---

### Post by bbengs on 2007-12-29
I've got the exact same issue with a All-In-Wonder on a 7.10 install.  Any help would be appreciated.

Thanks!

---

