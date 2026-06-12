---
title: "FN keys work, but volume keys don't! (Dell Inspiron)"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by H.E. Pennypacker on 2006-09-11
Arggh! Ever since installing Ubuntu, I've never been able to get my laptop's volume keys to work.  I'ved tried following all sorts of guides, Googled the topic, and even searched on Launchpad.  Nothing!

I've tried so much, but it seems everyone's case is different.  There's not a single person with identical problems, and some people's problems "disappear."  HOW?!

My FN keys work with increasing/decreasing backlight and the standby/hibernate keys, but the volume keys don't.

Uh, please help me solve this problem.

Dell Inspiron 2200
Ubuntu GNU/Linux 6.06
Intel ICH6
Sigmatel STAC9752.53

---

### Post by UltraMathMan on 2006-09-12
Try mapping them under System->Preferences->Keyboard Shortcuts

-Hope this helps :)

---

### Post by H.E. Pennypacker on 2006-09-12
I've tried that, and a host of other things.  Nothing's worked so far.

I've tried changing the keyboard layout too.

---

### Post by mscherzer on 2006-09-12
Hi,
I got the multimedia keys on my Inspirion 9400 working for the first time ever (they never worked under windows) under ubuntu.

Using gnome the volume levels worked out of the box but with KDE I had to use the following guide. That got all media keys working.

[http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/](http://www.tannerstokes.com/2006/08/02/getting-those-multimedia-keys-to-work-in-kubuntu/)

Might be worth giving it a shot.

cheers

Marcel

---

### Post by H.E. Pennypacker on 2006-09-15
Marcel, thanks a lot for that guide.  It worked wonders, but as I explained in a comment on that page, there's still a problem with raising the volume.  There's an apparent cap on raising the volume, while lowering the volume will go to the bottom of the bar.  Raising the volume with the keyboard keys won't actually raise the volume all the way to the end (top or right, whatever you consider top) of the volume bar.  It seems to be capped somewhere...as if there is a ceiling for raising the volume.  It only fills a fraction of the bar.

Btw, I use Gnome, and those instructions worked for me, except the raising volume part, slightly.

---

### Post by nalmeth on 2006-09-15
Maybe the volume keys are only adjusting the PCM volume or something?
Open the volume cpntrol to see whats actually happening

---

### Post by TMU on 2006-09-15
Hi!

I had(!) the same problem with master and PCM and I found a perfect HOW-TO written by LadyDoor.
[http://ubuntuforums.org/showthread.php?t=237408&highlight=master+pcm]("http://ubuntuforums.org/showthread.php?t=237408&highlight=master+pcm")
It works for me on a ASUS W1n. Just follow the guidelines and you'll be happy.

Regards, TMU

---

### Post by H.E. Pennypacker on 2006-09-16
TMU, I believe LadyDoor actually did more than what was necessary, but that's another point.  There's a way to merge PCM and Master Volume so raising one will raise the other, but like I said, that's for another thread.

Her guide did not help my raising volume problem.  The volume is still capped somewhere, and this only affects raising the volume.

---

### Post by elettronicha on 2006-09-16
Did you try [this]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hotkey&fullsearch=Testo") yet?

---

