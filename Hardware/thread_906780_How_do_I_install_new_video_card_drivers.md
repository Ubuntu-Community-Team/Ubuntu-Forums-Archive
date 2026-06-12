---
title: "How do I install new video card drivers?"
date: 2008-08-31
forum: Hardware
---

### Post by Mac_09 on 2008-08-31
I have xubuntu and my built in video card is an Intel 82810 (CGC).  How do I download the latest drivers for this video card and please give a link to where I'm supposed to find the dowload.

---

### Post by az on 2008-08-31
In GNU/Linux, you don't do things like that.  The drivers are part of the kernel - if you are up-to-date with software updates, your kernel is up-to-date.  If you are running the most current version of Ubuntu and your hardware is not properly supported, you may need to file a bug report to fix the problem.

That being said, Intel video cards are very well supported - better than the other kinds of video cards that have binary-only drivers.

What problem do you have with your video card?

---

### Post by Mac_09 on 2008-08-31
I can't run some of my favorite games.  This happened back when I had xp but I just updated the drivers and the games ran fine.  So I think I need to manually updated the drivers to get them to work smoothly again.

---

### Post by Rocket2DMn on 2008-08-31
You are using the "intel" driver by default, there are no other drivers.  What is happening when you try to run games?  If it is just really slow and laggy, turn off compiz before you play.

PS: Good to see you again, az, I haven't seen you around in ages.

---

### Post by Mac_09 on 2008-08-31
yes it's just very slow and laggy so how do I turn off compiz?

---

### Post by Rocket2DMn on 2008-08-31
To enable metacity and disable compiz, run
```
metacity --replace &
```
Then to re-enable compiz when you're finished, run
```
compiz --replace &
```
I made launchers in the taskbar for these.
You can also download and use an applet called fusion-icon (available in the repositories).

---

