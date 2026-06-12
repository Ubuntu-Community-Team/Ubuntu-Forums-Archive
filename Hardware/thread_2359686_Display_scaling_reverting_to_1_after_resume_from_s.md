---
title: "Display scaling reverting to 1 after resume from suspend?"
date: 2017-04-26
forum: Hardware
---

### Post by gilgongo on 2017-04-26
I've recently done a clean install of 17.04 on a machine with an Nvidia 750Ti card and a Dell 4K monitor. I'm using the Nvidia binary driver 381.09. This works great apart from the fact that the display scaling I set in the Ubuntu Screen Display settings always reverts back to 1 when the machine resumes after suspend. I need to set it at 1.5 otherwise everything goes tiny (BTW why doesn't Ubuntu scale to a sensible default with 4K monitors?)

Does anyone else get this? I can't find any mention of it elsewhere.

BTW I've tried the Nouveau driver and that doesn't wake up my screen at all after suspend. So that route's a non-starter. Never had any luck with Nouveau. Maybe a few more years...

***EDIT**: Damn - I've just discovered askubuntu.com which may be a better place for this... Hm. Hope I don't get flamed for cross-posting.*

EDIT: Looks like it's [been reported as a bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1689356") - will wait to see if there are any developments. Can't believe I'm the only 17.04 user with a HiDPI screen...

---

### Post by berin.larson on 2017-10-18
Having to reset the scaling every time is super annoying.
This bug makes me consider switching to 16.04

---

