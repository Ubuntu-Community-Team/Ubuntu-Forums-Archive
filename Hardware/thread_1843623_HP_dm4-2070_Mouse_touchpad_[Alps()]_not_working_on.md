---
title: "HP dm4-2070 Mouse touchpad [Alps(?)] not working on Ubuntu 11.04 64-bit"
date: 2011-09-13
forum: Hardware
---

### Post by GarlicGoldfish on 2011-09-13
Hello, I recently installed Ubuntu 11.04 64bit on my HP-dm4 2070 laptop.

Everything seems to be working fine except I have a huge problem with the touchpad.

It is very erratic to the point it is unusable.  It jumps(almost randomly) from point to point with the slightest touch and does not move in the direction I want it to at all.

The weird thing is there has been one or two instances when the touchpad was working flawlessly for a period of time.  Which leads me to believe that this is a problem that can be fixed. 

I've tried changing all the mouse settings in ubuntu with no luck at all.  I've also searched the forums on this topic and some people with the dm4 do not seem to have a problem with the touchpad, and while others have reported the problem I have not been able to find a clear solution how to fix it.

Any help would be greatly appreciated!
Thanks in advance.

---

### Post by justme0406 on 2012-01-07
i have a very similer problem, i have a dm4 2180ca and only 32 bit ubuntu and i have to restart ubuntu a few times to get it to work, and when it does no multitouch even though its selected and no edge scroll when its selected, when its not working its so unusable, i cant control it at all, it just jumps left and right randomly and clicking things at the same time, so useless. please help

---

### Post by mooselander on 2012-01-16
This worked for me, using 11.10 x64 on an HP DM4-2180:

[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

Both two finger and edge scrolling are working.

---

### Post by neutrl on 2012-01-16
> **mooselander said:**
> This worked for me, using 11.10 x64 on an HP DM4-2180:
[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

Both two finger and edge scrolling are working.
Thank you, this has worked for me for scrolling.  I can now disable tapping too.

Have you found anything that helps with palm detection?

---

### Post by mooselander on 2012-01-31
> **neutrl said:**
> Thank you, this has worked for me for scrolling.  I can now disable tapping too.

Have you found anything that helps with palm detection?

No, unfortunately I haven't.  To make matters worse, the dm4-2180's touchpad is offset to the right of the notebook (and I'm right handed) so I had to adjust my typing style to keep my palm off the touchpad (or bad things happen).

---

