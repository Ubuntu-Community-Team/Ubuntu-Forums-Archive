---
title: "Wacom Pen&amp;Touch sluggish, but not everywhere"
date: 2010-06-09
forum: Hardware
---

### Post by thegeologician on 2010-06-09
Hi all sorry for the long post. I use a Wacom Bamboo Pen&Touch tablet (model CTH460/K). I had it running on Karmic Koala before, by manually installing the kernel module from linuxwacom 0.8.6-2 from linuxwacom.sourceforge.net.
Then I upgraded to Lucid Lynx. As much discussed, it doesn't work out of the box. I tried installing the suggested xf86-input-wacom (0.10.6), but it didn't work. I tried the "old" method with the kernel module (as in 9.10), and it works quite nicely. :-)

With the following issues:
- no touch gestures, no touch-click (tapping) - I don't care so much, don't use touch a lot
- one annoying problem is this: pen and eraser work well, including pressure sensitivity in e.g. Inkscape, and overall as a mouse replacement. But in GIMP, the cursor follows only very sluggish, with a delay that gets longer the longer the brush stroke is (looks like a slow buffer). The weirdest about it: it depends on the position on the screen! It is very sluggish at the top, and almost perfectly responsive at the bottom!

I tried this with the drawing window full sized, or a small window moved to an upper and lower position; with absolute and relative mode for the pen; in relative mode on different positions on the tablet itself - all the same, it is the screen position.
Tips about switching on and off cursor outline and tool cursor in the preferences, which I read elsewhere for sluggish GIMP brushes, didn't make (much?/any?) difference.

I didn't have the tablet very long before I upgraded, and didn't test it a lot in GIMP then, but I remember having been impressed by the fluid movements, and can't remember any of this behaviour in 9.10. Because it's screen-position dependent and seems to have changed with the upgrade, I suspect a driver problem and post this question here, rather than in a GIMP-specific forum. Any ideas?

---

### Post by Favux on 2010-06-10
Hi thegeologician,

So far the only thing I've found is changing from what I think is the default:
```
xsetwacom set "your device name" or ID # RawSample "15"
```
to:
```
xsetwacom set stylus RawSample "30"
```
35 actually works better in Gimp, almost no lag.  But it makes it too jittery elsewhere.  Do the same for eraser.

Obviously not a great solution but it kind of works.

---

### Post by thegeologician on 2010-06-11
Thank you Favux, for the answer!

I found that RawSample was set to "2" on my system originally. As I said, this works fine in Inkscape. In GIMP I found I need to increase it to ~60 before I get proper responsiveness, but as you pointed out, it gets very jittery then, like snapping to a drawing grid.
I start to suspect GIMP again more than the wacomlinux driver... Not quite sure how to test it, though. Do you happen to know of the differences in the GUI-architecture of these two programs? But actually, this is not the right Forum to ask this question...

Anyway, thanks again!

---

### Post by Favux on 2010-06-11
Hi thegeologician,

Glad the "fix" works for you.  I'm going to play around with it some more.  If I don't get anywhere in the next week or two I'm going to try and ask a Gimp dev. I know and hope she answers.

---

