---
title: "Touchpad palm detection measurement"
date: 2018-04-25
forum: Hardware
---

### Post by ward388 on 2018-04-25
While typing on the keyboard of my laptop, sometimes sudden things happen because I accidentially touched my touchpad.

In KDE System settings > Input > Touchpad, I've selected the option "Disable touchpad while typing".
That prevents a lot of weird touchpad commands while typing.

...but somethimes, when I type a bit slower (like when I'm thinking for a few seconds about what to write and my hand are still above the keyboard), then unintended touchpad touches result in my mouspointer randomly clicking on my screen :mad:

I think that I can solve that by having good palm detection measurements.

In Kubuntu KDE I can configure "minimum width" and "minimum pressure" for palm detection. But how do I know what settings are good for me?

Trying all kinds of settings takes a lot of time and effort.

Is there a way to measure width and pressure? That I can touch my touchpad a number of times, and then the width and pressure values of every touch are shown?

___
Update: I use Kubuntu 16.04 LTS.

---

### Post by mircsicz on 2018-04-27
There's a way to monitor that with either xinput or evtest. I don't rememeber exactly but read that it's possible

---

### Post by ward388 on 2018-04-28
Thnx! It looks like that might work
...but it also looks quite complex to dive into. So I'm just going to find good settings with trial and error... :-(

---

