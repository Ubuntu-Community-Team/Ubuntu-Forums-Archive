---
title: "erratic/jumpy mouse using pointing stick or touchpad on Dell Latitude D620, Karmic"
date: 2010-03-13
forum: Hardware
---

### Post by meonkeys on 2010-03-13
My mouse pointer was moving slowly, then jumping, either when using the touchpad or the pointing stick. 

I'm running Karmic (9.10). This is not a fresh install, I've upgraded a few times.

The behavior seemed as described in [https://bugs.launchpad.net/bugs/296610](https://bugs.launchpad.net/bugs/296610) .

Removing irqpoll from the kernel command line appeared to solve the mouse movement problem.

However, I had originally *added* irqpoll because it appeared to fix very slow performance after resuming from sleep ( [http://ubuntuforums.org/showthread.php?t=1417770](http://ubuntuforums.org/showthread.php?t=1417770) ), so I'm not sure if that will now be broken again.

---

### Post by Phrea on 2010-03-13
Forgive me for being a bit obvious, but have you tried cleaning your mousepad and/or pointing stick?

I've seen similar problems, due to .. euh .. filth.

---

### Post by meonkeys on 2010-03-13
> **Phrea said:**
> Forgive me for being a bit obvious, but have you tried cleaning your mousepad and/or pointing stick?

Good question! The keyboard, touchpad, and pointing stick are all gunk-free. I rarely use them since the laptop is usually docked.

Also, since the effect of changing the kernel command line is immediate, it seems likely that's the culprit.

And it does appear the *removing* irqpoll means horrible performance on resume, so I won't be using suspend anytime soon. :(

Also see [this thread about what irqpoll helps]("http://ubuntuforums.org/showthread.php?p=8963744").

---

