---
title: "Jaunty xfix boot error"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by _goatboy_ on 2009-05-05
New user here, first of all.  I have read the forum several times in the past to fix issues and you guys always seem to have what I am looking for, so I finally decided to actually sign up and contribute back.  But first, I have a problem.

I (like many people) recently upgraded from 8.10 to 9.04.  Now when I say "upgraded" I mean I tried to upgrade from the update manager, got some weird graphical errors when I tried to log in to the new system, and ended up doing it via the CD instead.  Now it works just fine, except for one thing:

When I come home, I usually just push the power button with my toe (Weird, I know, but it works), get some coffee, and about a minute later I have a login screen waiting for me.  At least that was the case with 8.10.  What I get now is the splash screen followed by nothing.  All black.  To remedy this, I must first boot into Recovery Mode, run "xfix - attempt to fix graphical errors" or whatever it is from the dialog, and THEN boot normally.  Not a terribly long process, but something I'd like to avoid having to do each time I want to log in.

Background info:  I have already removed compiz-core (My graphics card sadly can't handle the default special effects) so I don't think that's a problem.  The computer is a bit older, but runs Linux just fine once I get it up and running.  Any other relevant information will be supplied upon request.

Thanks in advance for any help.

---

### Post by _goatboy_ on 2009-05-07
Bump.

I've Googled a bit and haven't really found anything of much use.  That may also be because I don't exactly know what the problem is on a technical level.  I also looked at the boot logs, but again I don't quite know what to look for, so this is hard for me to fix.

Anyone had a similar issue that may have a solution?  Thanks again in advance for any help.

---

### Post by _goatboy_ on 2009-05-12
Bump.  This is going to be my last self-bump before I let this thread die for a bit.

---

### Post by agathian on 2009-05-12
When this happens (before you go thru the fix operations) do you see any error in the /var/log/Xorg.0.log ?

you could use ctrl-alt-f1 to login thru command line to check/grab the log file.

---

