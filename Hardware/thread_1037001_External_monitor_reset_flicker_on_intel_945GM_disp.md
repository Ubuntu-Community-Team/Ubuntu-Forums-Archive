---
title: "External monitor reset flicker on intel 945GM display"
date: 2009-01-11
forum: Hardware
---

### Post by charles.figura on 2009-01-11
System: Intel 945GM on Dell Latitude D620, running Kubuntu Intrepid up-to-date.
Problem:  External monitor displays correctly, can be resolution configured, but screen blanks black, and redisplays on regular 10-second cycle.  I get about 8 seconds of display, then screen blanks for 2 seconds, then displays again.  The 10-second cycle appears VERY steady - I've been watching this go for about 20 minutes, keeping track of the display, and there's no creep - it's been flickering off right around the 7 second mark, flickering back on right around the 9 second mark.

This is obviously a pain if I'm trying to use an external monitor, it's impossible as I use my laptop and a data projector to teach classes.

My system is upgraded from Kubuntu Hardy.  I've tried reconfiguring, but there doesn't seem to be anything to reconfigure.  /etc/X11/xorg.conf is effectively empty, nothing particular to my system.  /var/log/Xorg.0.log shows no errors (that I can see)

I haven't found any bugs posted about this, so the big question is, is this some kind of residual configuration issue?  Something that I need to try reinstalling/reconfiguring?  I'd like to NOT have to reinstall the whole system, so if there's something I can remove/delete/reinstall, that would be great.

This has been going on for a while - I have 'made do', but would like to resolve the problem if possible!

Any ideas?

---

### Post by cefn on 2009-01-30
I can report identical symptoms on intel 945gm with kubuntu

---

