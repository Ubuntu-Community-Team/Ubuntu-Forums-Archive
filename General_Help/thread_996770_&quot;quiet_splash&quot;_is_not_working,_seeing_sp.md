---
title: "&quot;quiet splash&quot; is not working, seeing splash anyway"
date: 2008-11-29
forum: General Help
---

### Post by HousieMousie2 on 2008-11-29
I can't seem to get rid of the splash screens (start-up and shut-down.)

Not sure what changed or where it was changed at, menu.lst still says quiet splash, like it always has.

I think the culprit is somewhere in my /home partition, but I don't know where... since it is still refusing even after a fresh install (retaining my /home partition.) {{{ lol  I did not reinstall because of a splash screen issue. lol  I was having kernel panics after Adept botched an update.}}}

My System Setting, Splash Screen is set to none (using the GUI.)

I have found a ton of posts and pages for the opposite problem... when someone wants a splash screen but isn't getting one, but haven't had much luck finding information on trying to get rid of the splash screen, other than editing GRUB with the obvious quiet splash.

Thank you!

---

### Post by __Ryan__ on 2008-11-29
The "quiet" and "splash" keywords do completely different things.

To get rid of the splash screen comment out the "splash" keyword.  You can either remove it or place a "#" in front of it.

BTW, the quiet keyword limits the verbosity of the boot messages which you will see once the splash screen is not displayed.

Good Luck

---

### Post by HousieMousie2 on 2008-11-29
Ah, I see said the blind man...  lol that would mean there are a number of posts that are telling people that the two words go together. lol

Thank you for enlightening me, I will do my best to pass it on!

Odd, I wonder what changed, since mine had always said quiet splash...

Oh well, I can fix it now and that is all that matters.

Thanks!

---

