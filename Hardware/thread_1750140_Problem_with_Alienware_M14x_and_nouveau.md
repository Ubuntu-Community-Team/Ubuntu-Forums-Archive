---
title: "Problem with Alienware M14x and nouveau"
date: 2011-05-05
forum: Hardware
---

### Post by mad14x on 2011-05-05
Delete me.

---

### Post by mad14x on 2011-05-05
Shameless bump :(

---

### Post by mad14x on 2011-05-06
was able to fix the issue by removing the following package.

xserver-xorg-video-nouveau

---

### Post by mad14x on 2011-05-08
well seems the fix i have found works temporary.

if you were playing a game in windows and rebooted back to ubuntu.

i still get the issue where half the screen is white.

i unplugged the ac adapter and booted in ubuntu correctly.

this automatic video card switching is very wierd and not working imo.

---

### Post by foips on 2011-05-09
Exactly the same problem here on the same notebook. I'm wondering if you could help by explaining how to do that temporary workaround?

---

### Post by mad14x on 2011-05-18
> **foips said:**
> Exactly the same problem here on the same notebook. I'm wondering if you could help by explaining how to do that temporary workaround?

what i have done to make sure it works.

> sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-intel

unfortunately you might have glitches in video, but it works.

i also tried to disable the card with an acpi call but i still get the screen glitch at startup.

---

### Post by mad14x on 2011-05-18
also, i have tried the [http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/)
but it doesn't work.

but it's promising.

---

