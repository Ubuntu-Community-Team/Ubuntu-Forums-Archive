---
title: "ALSA and multiple soundcards"
date: 2005-01-26
forum: Hardware &amp; Laptops
---

### Post by ba747heavy on 2005-01-26
I have two soundcards in my box, and Ubuntu did a fine job of detecting them.  However, it is defaulting to the wrong soundcard as the primary.  I googled for any hints as to how to change this, and I also looked at the various config files I could find, but nothing jumped out at me.  So how do I have ALSA default to my other soundcard?

Thanks.

---

### Post by ba747heavy on 2005-01-27
Alright, guess my question was somehow silly.

---

### Post by marikka on 2005-01-28
I had similar problems with my integrated soundchip and my tv-tuner card. They got detected in the wrong order during boot.

I solved the problem by adding a few lines to /etc/modules

see this thread: [http://www.ubuntuforums.org/showthread.php?t=11190](http://www.ubuntuforums.org/showthread.php?t=11190)

It's just a guess, but if the cards are detected in the order they are in the PCI bus, you might just swap the physical order of the cards.

---

### Post by ba747heavy on 2005-01-28
Thank you, that did in fact work.  

Thanks again!

---

