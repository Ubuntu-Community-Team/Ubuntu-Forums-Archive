---
title: "X settings error"
date: 2009-09-07
forum: Hardware
---

### Post by m0ar on 2009-09-07
Hi there!

I'm having real truouble with my Acer 5738G, GeForde G105M!
I try to setup a dual screen config, wich only renders my taskbar useless ;s
Even if I close the Nvidia X Server Settings it's still in the taskbar and no new windows i open show up there!


The second problem is that X refuses to save my settings to xorg.conf; "Failed to parse existin /etc/X11/corg.conf!", EVEN when I start it my gksudo nvidia-settings!


I don't know that else to write, feel free to ask what I'm missing to tell ;)

Thanks!


Also: I'm using Linux Mint!  (Should be almost perfectly compatible with ubuntu from what I know tho ;P)

---

### Post by Fafler on 2009-09-07
> **m0ar said:**
> "Failed to parse existin /etc/X11/corg.conf!"

It doesn't really say that, does it?

Anyway, try posting your xorg.conf

---

### Post by m0ar on 2009-09-07
> **Fafler said:**
> It doesn't really say that, does it?

Anyway, try posting your xorg.conf


Exact quote is; Failed to parse existin X Config file '/etc/X11/xorg.conf'!


[http://pastebin.com/m7c4e0bd2](http://pastebin.com/m7c4e0bd2)

Thanks for the quick reply! <3

---

### Post by m0ar on 2009-09-08
I'd really need help on this one !


Thanks

---

### Post by RabidWeezle on 2009-09-08
what version drivers? and perhaps, just running sudo nvidia-xconfig again, and have it wipe out the old config totally, or rename the old config then run nvidia-xconfig/restart gdm and see what happens.

---

### Post by m0ar on 2009-09-08
> **RabidWeezle said:**
> what version drivers? and perhaps, just running sudo nvidia-xconfig again, and have it wipe out the old config totally, or rename the old config then run nvidia-xconfig/restart gdm and see what happens.
 
 
Will try when I get home, I'll post the results here :)

---

### Post by m0ar on 2009-09-10
> **RabidWeezle said:**
> what version drivers? and perhaps, just running sudo nvidia-xconfig again, and have it wipe out the old config totally, or rename the old config then run nvidia-xconfig/restart gdm and see what happens.


Worked, now i can write to xorg.conf, thanks for that.

The main problem remains tho, when i try to use TwinView my whole taskbar freezes, becomes totally uninteractable ><

Any ideas?

---

