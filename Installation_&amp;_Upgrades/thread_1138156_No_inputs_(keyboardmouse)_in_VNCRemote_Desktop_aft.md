---
title: "No inputs (keyboard/mouse) in VNC/Remote Desktop after Jaunty upgrade (from intrepid)"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by destr0y on 2009-04-26
Hi all,

I upgraded my PC this afternoon (via the alternate CD) to Jaunty/9.04 and have noticed that when I remote desktop into my PC since the upgrade, keyboard & mouse input is not working.

Not sure if its relevant, but I'm remoting from UltraVNC 1.02 on a winXP box.  Any ideas?

Cheers,
Brett

---

### Post by nhasian on 2009-04-30
its a confirmed bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

---

### Post by thecoolcat on 2009-05-30
Is there a fix for this or a workaround (other than turning off visual effects in compiz-fusion)?

---

### Post by nhasian on 2009-05-31
yeah there is the nodamage workaround which basically makes vino refresh the entire screen instead of only the part of the screen thats been changed (damaged). but as you can imagine it really slows down the response time.  I'm still waiting for a fix from compiz.

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

### Post by epolin on 2010-07-09
Thank you jmap for your script!
I suggest pgrep metacity to prevent any ambiguity

---

