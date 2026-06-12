---
title: "Detect changes to HDMI display (eg display switched to different input.)"
date: 2014-05-09
forum: Hardware
---

### Post by Jamey_Campbell on 2014-05-09
I'm running 14.04, using an Nvidia card connected to a TV over HDMI. I'd like to be able to detect when the TV is switched to a different input source to trigger a couple of scripts (either through events, or just polling.)

I haven't been able to find a lot of useful info while searching around.

"gddccontrol" sounds like the most suited to the task, but I'm having trouble getting it to compile. From what I could tell, it sounds like it may depend on using i2c for the queries, which I'm skeptical of the TV supporting. (I don't have i2c modules loaded though, and haven't tested this for sure.)

Other things I've seen suggested for similar situations and have tried include:


[LIST]
[*]get-edid - Doesn't see the display, period. (aforementioned lack of i2c may be the issue here.)
[*]nvidia-settings - I used various queries, including querying "all" with no useful changes. Diffing an "all" query when the display was active vs when the display was switched to another input only yielded a single change, in the "GPUUtilization" property - it was '0' while the display was on another input. I'm doubtful this is useful, and suspect the GPU idling would also yield a 0 result.
[*]udevadm / udev logs, etc. No luck here. Didn't expect udev to notice these events anyway.
[*]xrandr --query - Doesn't yield any differences when the display is on another input.
[*]xset q - Also yields no differences
[/LIST]

It is worth noting that I'm using audio over HDMI, but I don't think there's any useful way to query this - I believe the audio sink still exists while the TV is on another input, but haven't tested that to be certain.

Hopefully someone else has some suggestions, it seems like this would be something the system would be able to detect.

---

