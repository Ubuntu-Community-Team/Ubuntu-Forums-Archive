---
title: "Hardware audio w/ Asus Z87 mobo not working, 14.04"
date: 2015-06-03
forum: Hardware
---

### Post by james138 on 2015-06-03
I'm having issues with my fresh install of 14.04. Hardware audio comes through choppy and distorted. HDMI audio and my wireless headphones both work perfectly. When in sound settings, the 'Headphones' option disappears and reappears extremely frequently, and when clicked on causes the window itself to frantically change size. All returns to normal when a digital option is selected.

I had found a thread (that I've subsequently completely lost) that suggested that this was due to an incompatibility between the specific audio hardware Asus uses in their Z series mobos and the kernel version included in 14.04, so I tried updating my kernel to 3.18.3-031803 (amd64 on a 64bit system) manually and it failed to boot, so I purged it.

Also tried the fixes outlined in [This Thread]("http://ubuntuforums.org/showthread.php?t=2280517&highlight=asus+audio") with no success (specifically [this page]("https://wiki.ubuntu.com/Audio/PositionReporting")).


Does anyone have experience with this particular issue, or can point me in the right direction? I'm as green as the coffee implies, so any assistance would be greatly appreciated.

Update: I reinstalled the 3.18.3 kernel and it worked, however the issue is still present.

---

### Post by james138 on 2015-06-04
Really? Nobody has any experience with this problem?

I know the mobo is fine because it works like a dream in Windoze.

---

