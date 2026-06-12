---
title: "[SOLVED] Updated Kubuntu, display doesn't work."
date: 2008-11-28
forum: General Help
---

### Post by itsStephen on 2008-11-28
So this morning I'm told there's 13 updates available so I downloaded them. 1 of them happened to be the 2.6.27-9 kernel.

After restarting the computer I didn't get any display so I typed startx and I'm told that no screens were found. Above it was something about the Nvidia package or something and my graphics aren't supported (GeForce 6150SE).

I restarted and went to the grub menu and the older kernel is still in there so I'm using that for now.

How do I get my graphics to work with the new one? Did anyone want me to get the whole error? If I can't fix it then how do I get rid of the new kernel?

---

### Post by itsStephen on 2008-11-28
Fixed it.

For anyone that may want to know:

What I did was uninstall the nvidia driver and then boot into the new kernel. Then I reinstalled the nvidia driver and voila

---

