---
title: "Graphics driver randomly switching on 13.04 w/ Sandybridge - how to disable gallium?"
date: 2013-07-05
forum: Hardware
---

### Post by Ranko Kohime on 2013-07-05
Caveat: I'm running a custom build from the minimal ISO.  I use the Awesome WM.

Previously this system has been very good about the graphics, with 11.04, 11.10, 12.04 and 12.10 all having no issues.  However, when I freshly installed 13.04 last week, I've been having random issues with the graphics driver.

The only place I've found that actually gives me the info on the driver is the details section in gnome-control-center.  Sometimes it will come up with the correct driver (for which it does not give me name and version, but merely says "Sandybridge Mobile Graphics"), and other times it will come up with the Gallium driver, as follows: "Gallium 0.4 on llvmpipe (LLVM 3.2, 256 bits)"  There doesn't seem to be any predictability to it, and it can actually switch mid-session.  It does not generally do it when I can notice it, but rather at other times, for example, overnight when I am not using the system for long periods of time, (I have network jobs that run overnight, so it usually stays on), or if I put it to sleep.

lsmod does not reveal any modules loaded with either the keyword gallium or llvm, so I doubt that blacklisting gallium kernel modules will have any effect, as they're not being loaded anyway.

I'm open to suggestions.  :???:

---

### Post by Ranko Kohime on 2013-07-06
I'm going to tentatively mark this as solved.

I added myself to the video group and all seems to be well.

But I am left confused as to why I could even start an X session at all without that membership, or, if the current state of affairs is that you can start an X session in that state, why the graphics weren't consistenly forced to gallium.

---

