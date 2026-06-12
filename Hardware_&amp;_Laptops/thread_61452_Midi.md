---
title: "Midi?"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by mpt1313 on 2005-08-31
I am not only new to ubuntu, but also VERY new to linux. I want to continue not supporting microsoft, but I like to make music on my computer. I can get tracker type apps to work, but if I try to use any sort of external midi control, I get nothing. I have to different keyboards, both usb, and I can't seem to figure out how to get it to work. Can anyone please point me in the right direction.
mpt

---

### Post by Kremlin on 2005-09-04
[QUOTE=mpt1313]I am not only new to ubuntu, but also VERY new to linux. I want to continue not supporting microsoft, but I like to make music on my computer. I can get tracker type apps to work, but if I try to use any sort of external midi control, I get nothing. I have to different keyboards, both usb, and I can't seem to figure out how to get it to work. Can anyone please point me in the right direction.
mpt[/QUOTE]
Are you trying to use them by USB, or do you have another midi interface and you're running a midi cable between the keyboards and the computer?

If the first, then you may or may not be out of luck. Try modprobe'ing usb-audio, I believe if the controller is class compliant that should work. If not, you'll have to look around on the web for your particular keyboard type, and it's linux support.

If you have a midi cable solution, then it's a bit easier, you then have to get the midi input working. If you use something like the MAudio midiman or anything edirol/roland, it should be fine. If you use one on a soundcard, this should also work.

So try the midi cable way if you have that option, otherwise check out usb-audio and move from there.

---

