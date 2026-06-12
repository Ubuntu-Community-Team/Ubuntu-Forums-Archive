---
title: "Wireless USB Keyboard Can't Keep Up With My Slow Typing"
date: 2014-10-07
forum: Hardware
---

### Post by buzzingrobot on 2014-10-07
I recently picked up a Logitech wireless keyboard and  wireless mouse, the kind that use Logitech's USB unifying receiver.

Several times a day, the keyboard can't keep up with the characters I type, eventually spitting them out in one rapid string of characters.

E.g., when I typed the word "recently" above, nothing appeared on screen until I tapped the space key after tapping the 'y' key.

The Delete and Backspace keys are also affected. Sometimes no keystrokes at all register.

I'm on 14.10 Kubuntu, and I've seen it on Fedora 21 dailies, also.

It does not happen with a conventional USB wire keyboard.

Is this to be expected with wireless USB keyboards? Or, is something else going on?

Both 14.10 and Fedora 21 use their versions of the 3.16 kernel, if that's in play.

---

### Post by Vladlenin5000 on 2014-10-07
> **buzzingrobot said:**
> Is this to be expected with wireless USB keyboards? Or, is something else going on?

Something else, I think. All the RF wireless devices, keyboard or mouse or combos, I've tested so far worked as designed. OTOH, I've heard of too many users similar complaints about certain Logitech devices, particularly with the new standard, therefore I'm sure it's no coincidence.
The Logitech proprietary receiver probably needs some code to work properly. They usually do work flawlessly in the same PCs running Windows + Logitech software.

---

### Post by buzzingrobot on 2014-10-07
> **Vladlenin5000 said:**
> Something else, I think. All the RF wireless devices, keyboard or mouse or combos, I've tested so far worked as designed. OTOH, I've heard of too many users similar complaints about certain Logitech devices, particularly with the new standard, therefore I'm sure it's no coincidence.
The Logitech proprietary receiver probably needs some code to work properly. They usually do work flawlessly in the same PCs running Windows + Logitech software.

Thanks. I suspect I'll shop around.  I got fed up one afternoon with all the cords on my desk and ran out and bought the mouse and keyboard.  So far, the mouse has behaved.

---

### Post by Vladlenin5000 on 2014-10-07
I would search more, just in case, especially about the "unifying receiver" which seems to be the common denominator.
Perhaps the fine people at ArchLinux forums already found out something, who knows?

Currently I've no time for any extensive research and no way to test anyway.

---

### Post by buzzingrobot on 2014-10-07
I ran a quick search at Arch and saw threads pointing to alleged kernel issues with fixes involving kernel and/or module rebuilds.  I dunno about that, but I do know it's not 1998 so I won't be rebuilding any kernels. Lazy, too. :eek:

No worries, I have 6 other keyboards that have accumulated around here.

---

### Post by varunendra on 2014-10-07
Just to clarify, is this wireless keyboard/mouse set really "Wireless" (2.4GHz wifi device) or a bluetooth one?

I have used both kinds and the bluetooth ones did have some similar problems, but the wifi set (being used at my brother's home, can't remember the brand but a really cheap one) is working flawlessly for about an year. He uses windows, but whenever I visit him, I use either Ubuntu 10.04 installed on his computer, or 12.04 live USB, and it works as good as on Windows.

---

### Post by tgalati4 on 2014-10-07
If the Logitech wireless is indeed 2.4 GHz, then it might be a interference problem.  [Build yourself a faraday cage]("http://www.thesurvivalistblog.net/build-your-own-faraday-cage-heres-how/") and test the wireless keyboard inside it.  You will come out feeling refreshed without the exposure of alien brainwaves.  Post a picture of it.

---

### Post by buzzingrobot on 2014-10-08
The set isn't bluetooth.  It's USB wireless.  I've used bluetooth in the past; the delay of a few seconds before the keyboard and mouse became active after resuming from suspend was annoying. There's a shorter delay with this Logitech setup.

---

### Post by kurt18947 on 2014-10-08
I've noticed the same lagging issue.  I have a Logitech K320 keyboard and M570 trackball.  I really noticed the delay when using both devices on one receiver, about 8 seconds.  I even fired up Windows (took about 5 minutes short of forever to download and install the accumated updates - it'd been a while :p) and installed Logitech's unifying software. I didn't any difference.  What seems to have helped is to pair the keyboard with one receiver and the trackball with the other receiver. I got a receiver with each device obviously.  I still notice a lag occasionally but it's more like 1 second instead of several and it doesn't seem to occur as frequently as when having both devices paired to one receiver.

---

### Post by varunendra on 2014-10-08
> **kurt18947 said:**
> What seems to have helped is to pair the keyboard with one receiver and the trackball with the other receiver. I got a receiver with each device obviously.

Interesting. The one I mentioned comes with only one receiver. Both devices run on 3 volts, that is, 2 x AAA type batteries each. Range, about 8-10 meters across two rooms (doors open, but a 13" wall in the direct path).

I wish I were there to experiment with the latest kernels.

---

### Post by kurt18947 on 2014-10-09
> **varunendra said:**
> Interesting. The one I mentioned comes with only one receiver. Both devices run on 3 volts, that is, 2 x AAA type batteries each. Range, about 8-10 meters across two rooms (doors open, but a 13" wall in the direct path).

I wish I were there to experiment with the latest kernels.
I have two receivers because the keyboard & trackball were separate purchases. I'm allergic to mice :D.

---

