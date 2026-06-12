---
title: "question about having two soundcards"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by darkpark on 2005-07-03
in my computer, i have two soundcards: one that is supported in linux (via alsa) and another soundcard that isn't but is being detected as a different card than it really is.
anyway, i'd like to stop ubuntu from installing any drivers/modules for the unsupported soundcard (EMU 1212M which is being detected as EMU APS).
The othersoundcard is an M-Audio Revolution 7.1 (envy24ht) which i would like to get working.   

any help would be appreciated.

---

### Post by Lord Illidan on 2005-07-03
First...why do you have two soundcards?? Can't you do with just one only?

Second, what I did, when I was in a case like yours  was to put the soundcard working with Linux in the pci slot before the other soundcard (which worked only with WinXP)..

like this:

        -----AGP slot----
----PCI slot-----   Put soundcard of Linux here, which you want to install in Alsa
----PCI slot-----   Put second soundcard here!

---

### Post by darkpark on 2005-07-03
i'm a semi-audiophile so i have one soundcard that i use for listening with my headphones and a second one for games and other general things.


anyway, i just want to disable that EMU card in Ubuntu.  At the very least, I'd like to make the M-Audio card the default.

---

### Post by Lord Illidan on 2005-07-03
Ok then, viewing the motherboard from above...


    -----AGP slot----
----PCI slot----- Put M-Audio Revolution 7.1
----PCI slot----- Put EMU 1212M

Linux should detect and use the first one...
Windoze should detect both..which is what u want, apparently...

---

