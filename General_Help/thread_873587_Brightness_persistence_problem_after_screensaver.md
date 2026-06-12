---
title: "Brightness persistence problem after screensaver"
date: 2008-07-29
forum: General Help
---

### Post by pedrogent on 2008-07-29
I have a BenQ LCD. It's a lovely monitor. Small problem tho': using it is like staring at the sun. I use the buttons on the side to reduce the brightness to zero and it's still *way* too bright.

I've tried adding and using the Brightness Applet. This doesn't do anything at all.

So I've installed the nvidia-settings app (see below). This does the job nicely with (-0.60 brightness & -0.30 contrast). The problem is that if I go away and the screensaver comes on, when I come back and unlock the screen we're back at eye-scorching levels of brightness again and I have to manually reset it using nvidia-settings.

Anyone know of a way to make the brightness reduction permanent?

---

### Post by pedrogent on 2008-07-29
Anyone?

---

### Post by to young on 2008-10-29
I have the exact same problem.  Except my monitor is too dim.  I turn up the brightness.  but screensaver resets it.  

Please help on how to maintain the brightness.  

thank you.

---

### Post by margiwarg on 2008-11-04
I have the identical problem. Brightness settings reset at startup or when the screensaver kicks in. As soon as I open nvidia-settings they are restored. Any idea how to save brightness settings? Anyone? Other ppl also seem to have this problem: [http://ubuntuforums.org/showthread.php?t=929952&highlight=brightness+nvidia-settings+screensaver](http://ubuntuforums.org/showthread.php?t=929952&highlight=brightness+nvidia-settings+screensaver)

---

### Post by effenberg0x0 on 2008-11-29
I have the exact same annoying problem with Ibex on a DELL Vostro 1310 (Intel GMA 945).

Is there a way to define Brightness, Contrast, Backlight levels on xorg.conf or other conf file?

Regards,
Effenberg

---

### Post by Too Late on 2009-11-03
This is quite old thread, but I didn't find newer.

I have the same problem. When my Ubuntu starts up, the screen is first too dark. When the screensaver activates, the brightness changes to normal. (My screensaver starts with a "fadeout" and sometimes the brightness gets corrected immediately when the fadeout begins. Sometimes it gets corrected after that fadeout). Of course, it's hard to say which one is the "right one", but I've calibrated my monitor so that the screen is fine after a screensaver, because screensavers can't be "unstarted", so it's better to let the screensaver start one time than keep it not starting. Of course, I could completely disable screensaver and adjust my settings, but I don't want to do that.

I'm using Ubuntu 8.04, GeForce3 and an old 17" Hitachi LCD. I don't have nvidia-settings installed.

---

