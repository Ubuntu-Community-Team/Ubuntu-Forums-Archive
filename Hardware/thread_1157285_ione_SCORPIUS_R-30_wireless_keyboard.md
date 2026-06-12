---
title: "ione SCORPIUS R-30 wireless keyboard"
date: 2009-05-12
forum: Hardware
---

### Post by rhdinah on 2009-05-12
I've used this keyboard in Windows and it works flawlessly -- this is one of those USB wireless devices ... with a built in mouse touchpad.

Anyway, some combinations of keys, like CTRL-ALT-DEL are not recognized in Jaunty. You can see this behaviour in the keyboard shortcuts dialogue when setting a disabled entry. For example CTRL-ALT-DEL is recorded as ALT-DEL and others. Here's an interesting example:

CTRL-RIGHT produces CTRL-RIGHT
ALT-RIGHT produces ALT-RIGHT
CTRL-ALT-RIGHT produces ALT-RIGHT

Is this behaviour because of a bug? Is there a better keyboard match to overcome this behaviour? I currently have Generic 101-key PC selected as the keyboard model.

I've retested it with Windows XP on the identical system. Keyboard works properly. I've also tested it with PCLinuxos 2009 and Fedora 10 - identical problem as Ubuntu. I've also used it on my Ubuntu T60 notebook with the same behaviour. So I suspect it is a kernel deficiency.

Here's another anomaly:

CTRL-ALT-RIGHT keys pressed and held in that order produces ALT-RIGHT
ALT-CTRL-RIGHT keys pressed and held in that order produces CTRL-RIGHT

Thank you!

p.s. Should I submit this as a bug report?

------------------------------------------------------------------------------------

p.p.s. I'll be reporting this as a kernel bug in LaunchPad shortly as it seems the proper thing to do. Reported [here]("https://bugs.launchpad.net/ubuntu/+bug/376131").

---

### Post by rhdinah on 2011-03-02
Bug reported ... no developers interested I suppose ...

I guess the Andromeda virus will eat the plastic and rubber off my keyboard before a solution is affected. :(

---

