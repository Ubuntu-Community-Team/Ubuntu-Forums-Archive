---
title: "Miserable xmodmap failure"
date: 2008-09-09
forum: Hardware
---

### Post by NickLanam on 2008-09-09
There's an embarrassing amount of bumping and monologue in the other post I made about this, so starting fresh and hoping it doesn't end up on page 5 before I wake up in the morning and nobody's read it :P

I recently moved from Fedora 8 to Ubuntu 8.04. I've always loved Fedora, used it since 6, and had a nice little group of files to use xmodmap and gconf to change the keybindings of my Ideazon MERC ([link]("http://lib.store.yahoo.net/lib/xoxide/iz-merc-keyboard-2.jpg")).

In normal (as in not while I'm playing a game) keybindings, the numberpad on the left opened a wide range of applications thanks to Metacity's keybindings in gconf. This no longer works because an unbound key in xmodmap has no keysym and a bound key isnt listened to by metacity. A few keys now share keysysms too :(

But my big issue is with the red keys on the left. I can bind them OK, but for some reason, in XEV, these keys among my multimedia keys emit keyRelease events at the same time they emit the keyPress. Naturally, this causes problems with repeating even after xset r, and I can't play my favorite games and move properly.

I feel like I've started using Linux all over again, I'm totally helpless here, dropping to console and using showkey/dumpkeys/etc show everything is working fine (though curiously the broken keys don't repeat, but at least they go up at the right time in showkey)... Help please!

---

### Post by NickLanam on 2008-09-10
Time to start the embarrassing amounts of bumps again...

---

### Post by NickLanam on 2008-09-10
And again. 5 hours to get to the 3rd page, wow. I've gotta find the best time to post this such that someone sees it before 80 new topics bury it.

---

### Post by NickLanam on 2008-09-11
BUMP.
Please, let this be read before a million new posts drown it... Please!!?

---

### Post by NickLanam on 2008-09-13
Buuuuuuuuuuummmmmmmpppppppp

---

