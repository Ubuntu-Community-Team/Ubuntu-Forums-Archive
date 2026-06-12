---
title: "[SOLVED] Returning from: apt-get install xserver-xgl compiz"
date: 2008-08-01
forum: General Help
---

### Post by robnoyes on 2008-08-01
Hi,

I'm, sort of, just a beginner...I've had Hardy installed for a few months, but I'm not comfortable yet.

Yesterday, I attempted to install xgl compiz. Here's the cmd line: sudo apt-get install xserver-xgl compiz, which was supposed to put some cool graphics on my system and increase the speed. Neither happened! In fact, the speed got worse.

It's likely that my laptop has an older video card or drivers, but at the moment I don't have time to figure it out or hunt them down.

So, since I really need the little speed I had before the xgl/compiz install, what commands do I issue to return to how things were?

RobN

---

### Post by overdrank on 2008-08-01
> **robnoyes said:**
> Hi,

I'm, sort of, just a beginner...I've had Hardy installed for a few months, but I'm not comfortable yet.

Yesterday, I attempted to install xgl compiz. Here's the cmd line: sudo apt-get install xserver-xgl compiz, which was supposed to put some cool graphics on my system and increase the speed. Neither happened! In fact, the speed got worse.

It's likely that my laptop has an older video card or drivers, but at the moment I don't have time to figure it out or hunt them down.

So, since I really need the little speed I had before the xgl/compiz install, what commands do I issue to return to how things were?

RobN

Hi and to find you graphics card use the command ```
lspci
``` and look for VGA. As for removing xgl then can use this command 
```
sudo apt-get remove xserver-xgl
``` just replace install with remove.

---

### Post by robnoyes on 2008-08-01
Thanks

---

