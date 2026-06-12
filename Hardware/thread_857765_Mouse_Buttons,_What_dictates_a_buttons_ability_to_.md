---
title: "Mouse Buttons, What dictates a buttons ability to &quot;Hold&quot;?"
date: 2008-07-12
forum: Hardware
---

### Post by Leefmc on 2008-07-12
Well after a ton of effort, i damn near have all of my mx revolution woes taken care of, except one. The Middle Mouse Remap.

Now remapping the buttons themselves is easily done via xmodmap, however all of the buttons on my MX Revolution have a "Press" and a "Release" state.. except the left/right scroll buttons. Anyone know if there is a way to change them to accept a Pressing/Released workflow?

As it was in windows, i had MMB mapped to ScrollWheelLeft. This sounds awkward, but it works wonderfully. However currently it seems i cannot do this.. any ideas?

An example of what i mean, is if you load up xev, and press and hold each button and watch the output, remember, do not release right away until you clearly watch the output. Most of the buttons will say something like:
```

ButtonPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x87, subw 0x0, time 9854617, (94,66), root:(162,764),
    state 0x10, button 1, same_screen YES

```
and will not display the release event, until you let go. This is what you want for everything. The scroll left & right on the otherhand, will instantly shows the press and release event.

Any ideas on how to make the left & right scroll button a hold-type button?

Thanks,
Lee

(Note i'll be posting a condensed tutorial once i get it all done. This is the last step heh)

---

