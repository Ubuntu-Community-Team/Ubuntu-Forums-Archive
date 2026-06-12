---
title: "HOW TO: Configure your synaptics touchpad to a more tolerable level."
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by popophobia on 2007-11-02
Ok, I tried to figure out how to configure touchpad by GUI in Ubuntu for a week or so. All of which disappointed me. I switched to use a Bluetooth mouse instead. However, I came across [this site]("http://linux.die.net/man/5/synaptics") today and took sometime to configure the touchpad so that it works better.

I just want to share with you a few important parameters to config your tapping so that it does not annoy so much.

Make sure you have [SHMConfig turned on]("http://ubuntuforums.org/showthread.php?p=975421") to set these settings. You may need to reboot before the change takes effect.

First, we will be using synclient in Terminal.
```
synclient -l
```

Listed are the list of parameter for your touchpad.

To change the value, you have to type in
```
synclient PARAMETER=VALUE
```

They are all mentioned in the site. But there are a few you need to pay close attention to:

1. **FingerLow** and **FingerHigh**: define when your touch is a tap and when it's a movement. I set FingerHigh to ~30-35 so that it does not confuse between my "light touch" and my tap.

2.**MaxTapTime**: Lower if you tap faster. Also set it along with **FastTaps**, according to your personal preferences. All the changes take place right away, so, be sure to test them out as you set them.

3. **LockDrags**: when drag, you can take your finger off the touchpad and tap to release the object. This is useful.

That should take care of the tapping annoyance. There are more parameters and you can explore them as you wish. Some of them might be quite useful (conner tap and circling...)

I found that none of the GUI touchpad tool give you the option to fine tune as good. So, if you want to you your tapping with your touchpad, I'd recommend you spend 10-15mins fine tuning it.

ps: Since it's my first time posting some guide on Ubuntu, my second week in Ubuntu, so  please forgive my mistakes. Hope it helps.

---

