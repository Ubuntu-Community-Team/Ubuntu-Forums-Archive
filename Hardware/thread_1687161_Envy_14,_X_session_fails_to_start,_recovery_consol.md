---
title: "Envy 14, X session fails to start, recovery console all black"
date: 2011-02-13
forum: Hardware
---

### Post by afoglia on 2011-02-13
I had been running 10.10 fine on my Envy 14 until this morning.  Now, when I try to log in, the screen returns to tty1 and I get a bunch of "stimulus stuck in loop" messages, and then gdm restarts.  (This holds whether I tried to use gnome, IDE, or the recovery console.)  I tried booting the kernel in recovery mode,  but after the boot messages, I'm left with a totally black screen.  I've even tried older kernels, left from previous upgrades.

I tried manually switching to the discrete graphics from the command line, but that had no effect.

When I last used my computer, I had no new upgrades.  (I think I last upgraded on Thursday, and nothing new was available on last I checked.)  I had the computer on last night, and left it to suspend, but oddly this morning, the monitor was off, but the power light was on, implying only the screen shut off.

Any ideas how to approach fixing this?

---

### Post by afoglia on 2011-02-13
I've checked /var/log/messages, and the only messages that are produced are "Skipping EDID probe due to caches EDID" from the kernel, and "ratelimit.c: 1 event suppressed" from pulseaudio.  dmesg has the EDID probe messages and the atombios messages.

Also, I forgot to mention that I can still boot into Windows with no problem, so this is not a hardware issue.

(Now to figure out how to get my wifi working from the prompt, though that seems to require a GUI nowadays...)

---

### Post by afoglia on 2011-02-13
I just tried updating to 11.04, and that's made things worse.  On the plus side, the gdm restart is much quicker, on the negative side, printing to the tty is painfully slow, running at a few lines per second, or about three seconds just to output a screen of text.

---

### Post by afoglia on 2011-02-13
The problem was edits I had ade to my .profile.  Unbeknownst to me, and not mentioned in the comments in the file, the .profile is sourced by **dash**, not bash, when logging in.  Even in the default .profile created for new accounts in natty.

So now, I've upgraded and have half a dozen other problems that need to be fixed.  I might just wipe my system and reinstall.

---

