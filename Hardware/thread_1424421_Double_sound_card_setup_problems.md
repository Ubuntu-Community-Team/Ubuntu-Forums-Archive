---
title: "Double sound card setup problems"
date: 2010-03-07
forum: Hardware
---

### Post by schmidtbag on 2010-03-07
Just for some quick information, I have integrated sound and a separate sound card.  Both are fully functional.  I am using Xubuntu 10.04 (I'm using it for specific reasons, so I can't just simply downgrade to an earlier version to fix my problem), and when I type cat /proc/asound/cards I get the following:
```

 0 [AudioPCI       ]: ENS1370 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1370 at 0xc400, irq 18
 1 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at irq 18
```

and less /proc/asound/modules gives me:
```
 0 snd_ens1370
 1 snd_intel8x0
```

First, I would like to know - is it possible for 2 different users to use a different sound card using their own ~/.asoundrc file?

If so, to put it simply, how do I do this?  I've tried looking at tutorials on how to edit the file but they either are way too vague or theres something I'm doing wrong that it didn't tell me about.  The file originally never had anything in it.

I have tried using asoundconf-gtk, but that doesn't appear to work in Ubuntu 10.04 anymore.

---

### Post by schmidtbag on 2010-03-09
bump

---

### Post by schmidtbag on 2010-03-10
seriously nobody knows how to do this?

---

