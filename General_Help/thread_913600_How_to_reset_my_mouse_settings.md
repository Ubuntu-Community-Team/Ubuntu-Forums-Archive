---
title: "How to reset my mouse settings?"
date: 2008-09-07
forum: General Help
---

### Post by galvao on 2008-09-07
I've recently messed up my mouse settings on Ubuntu (Gnome) so now every once and a while my mouse double clicks when I click the button only once.

How can I reset my mouse to the default values?

TIA,

---

### Post by Darkade on 2008-09-07
Open a nautilus and look for preferences (I think it's in the edit menu, I'm on my laptop which only has openbox rightnow) and look for open links with one click or somethink like that.

I guess you could also run ```
xorgconfig
``` and that would reset your keyboard and mouse and monitor... and many things configs (and backup current ones) but I woulnd say you need to do that to fix your mouse. Leave as a last... very last resource

---

### Post by galvao on 2008-09-09
Thank you for your quick reply.

> **Darkade said:**
> Open a nautilus and look for preferences (I think it's in the edit menu, I'm on my laptop which only has openbox rightnow) and look for open links with one click or somethink like that.

Everything is ok in Nautilus, what I've changed were the settings under System->Preferences->Mouse

> **Darkade said:**
> I guess you could also run ```
xorgconfig
``` and that would reset your keyboard and mouse and monitor... and many things configs (and backup current ones) but I woulnd say you need to do that to fix your mouse. Leave as a last... very last resource

Yes, I could backup my xorg.conf, run xorgconfig and manually "merge" the old and the new conf files, but I'd really like to avoid that...

Any other suggestions?

Thanks again,

---

