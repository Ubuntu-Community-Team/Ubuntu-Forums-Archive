---
title: "Lost pairing w/ DiNovo Edge"
date: 2009-07-21
forum: Hardware
---

### Post by dclement on 2009-07-21
Hello,

I had succeeded in pairing my Logitech DiNovo Edge w/ my laptop (running Jaunty 64), first time. I had not used the Logitech dongle.

But today, the pairing was lost. I tried to do it again, with no luck. At present I'm using the keyboard with the dongle, but that is not 100% satisfactory.

In fact, it takes a few seconds for the keyboard to respond at login time, so possibly I just _thought_ the pairing was lost, and now my BT config is somehow corrupted.

I tried to reset the DiNovo-relevant part of the BT config, by editing the files in /var/lib/bluetooth, removing any mention of the keyboard. But that did not work.

I'd like to restart it from scratch. How can I do that?

TIA - best regards, Daniel

---

### Post by dclement on 2009-07-24
Hello again,

I have managed to redo the pairing by editing the sdp file under /var/lib/bluetooth. There was apparently an extra empty line.

Alas, the pairing got lost again. I was able do retreive it this morning, after completely erasing anything from the old BT configuration. I connected the keyboard first. Let's see if it lasts this time...

I have one more reason to try to connect without the dongle: the time lag at logon seems much longer *with* the dongle than without. Maybe *this* can be overcome by some clever setting?

---

