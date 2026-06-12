---
title: "HP dv3550el: Battery and brightness. Then I'm done!"
date: 2011-05-04
forum: Hardware
---

### Post by lolwhat on 2011-05-04
Hey guys, its been a long time since I felt the need to have a linux distro on my laptop, and now this is driving me mad! :)

I dont remember which version of Ubuntu I used to have on this laptop, but as far as I remember everything used to work fine (at least everything I cared about).

But now 2 bugs are really stressing me out:

1) *CRITICAL* upower incorrect battery status report.
2) ...someone said brightness? :D

I found a workaround using nvclock for the 2 even though its annoying to have to pass through the terminal every time I need to set a different brightness, considering that as soon as I suspend, lock the screen etc Ubuntu sets is back to 100% (When I use the hotkeys the popup shows but does nothing). Is there a way to edit the standard behaviour of the hotkeys maybe with scripts possibly without losing the notify/animation?

1 is really serious. When I boot up the laptop unplugged, upower always says "Fully charged" (and so does gnome-power-manager), but quering it with --dump tells in number that the battery is discharging. I suspect upowerd is not triggered on boot or something. Plugging the chord in however gets things back to normal.

Here's an upower --dump log:
[https://gist.github.com/954935](https://gist.github.com/954935)
As you can see if upowerd seems not to be notified to be on battery displaying "on-battery: no".

Any help is much appreciated. Thanks everyone in advance!

---

