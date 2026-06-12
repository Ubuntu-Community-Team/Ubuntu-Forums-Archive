---
title: "gameport joystick support broken in Jaunty upgrade"
date: 2009-04-24
forum: Hardware
---

### Post by Dodongo Dislikes Smoke on 2009-04-24
I've had my old gameport Gravis PC GamePad working in Ubuntu for a couple versions now.  However, now that I've upgraded to Jaunty it no longer works.  I've tested it in Mednafen, Stella, and Cave Story, each of which it once got along with perfectly.  As best as I can tell, all the required modules are still loaded (snd_trident, gameport).  Is anyone having any similar issues or might know of any potential fixes?

As it's not an analog controller, it wasn't effected by the big Intrepid joystick snafu (which finally seems fixed for x86, yay!).  I guess it had this coming...

---

### Post by sstakes1 on 2009-05-03
I see this [kernel bug 12426]("http://bugzilla.kernel.org/show_bug.cgi?id=12426")may be relevant. The patch alone did not work for me. I had to hack the gameport driver and got it to work as described in [thread 1145181]("http://ubuntuforums.org/showthread.php?t=1145181")

---

### Post by Dodongo Dislikes Smoke on 2009-05-08
Thank you!
I'm a little nervous about messing with kernel patches at this points.  Let's hope they fix it in the next kernel update.

---

