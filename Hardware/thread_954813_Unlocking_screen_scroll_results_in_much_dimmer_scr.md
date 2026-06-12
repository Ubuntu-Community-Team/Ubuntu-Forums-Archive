---
title: "Unlocking screen scroll results in much dimmer screen"
date: 2008-10-21
forum: Hardware
---

### Post by sforces on 2008-10-21
I'm running on a ThinkPad X61 with Ubuntu 8.04 x64.

Whenever I do a Screen Lock, when I come back from it (after typing in the password to unlock) 80% of the time the screen is MUCH darker than it was but the menus (Applications, Places, System) are at the brightness that it was (and is normal).

I don't have it set to auto dim, and it doesn't matter if I'm on battery or AC. The brightness app is set to the highest.

If I logoff and log back in it's back to normal until another screen lock.

I've also tried having no screen saver and that has no affect.

Any ideas how I can resolve this?

---

### Post by sforces on 2008-11-13
Upgraded to Intrepid and this issue appears to be gone. Unfortunately the new kernel that comes with Intrepid has it's own set of issues. Sigh.

---

### Post by aaronp on 2008-11-30
Hi all,
I have the same problem here but a bit more info.
This started happening after I turned on compositing in Metacity. I'm running Hardy 32bit. (not looking to upgrade to Intrepid at this point in time)

It seems to only happen when the screen has been locked for a while. If I just lock it and unlock asap it is ok.
The effect is the same as when pressing alt-tab to switch between apps and the 'inactive' app is dimmed out.
However, no combination of Alt-Tab makes any difference. As per the previous post, all of the menus come up in their normal brightness whilst the remainder of the screen stays dim.
The only way to resolve this as far as I can tell is by restarting Metacity - this fixes it instantly.

Any thoughts?

thanks
Aaron

---

