---
title: "No touchpad on Winbook a710"
date: 2008-07-12
forum: Hardware
---

### Post by NK-Magi on 2008-07-12
I've been trying to install Ubuntu 8.04 on a Winbook a710 that I was given that was running Fedora Core 6 perfectly fine.  I went through and reformatted and booted the LiveCD of Ubuntu and did the install but the touchpad didn't work at all throughout the full installation but I guess it would simply work after the full install of all the drivers but no luck there.

I also went and tried the 64-bit version with the exact same results.

I'm asking if anyone knows any easy way to get it running fine on the laptop or if anyone has tweaked theirs to get it running on it.

On a side note, even trying to use a simply USB mouse doesn't work on Ubuntu so theres no way of inputting any sort of mouse on the laptop.

---

### Post by NK-Magi on 2008-07-12
I've got it up and running now with a USB mouse so I can install updates and do editing alot easier but still wondering on how to install the touchpad easily.  Going to try gsynaptics soon after updates are installed.

---

### Post by NK-Magi on 2008-07-13
Still no change, any ideas?

---

### Post by thomasjw on 2008-07-25
I'm in exactly the same boat with you, man.  Winbook A710 AMD64, absolutely no touchpad response at all.  I've followed all the instructions I can find online that I have the skill to follow and still the touchpad just isn't happening.  i see a lot of discussion about people's touchpads being glitchy or erratic, but the only precedent I've found for one that doesn't work at all is the HP500: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96598](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96598)
and that problem was apparently fixed:
[http://use.perl.org/~dgl/journal/33263](http://use.perl.org/~dgl/journal/33263)

If this helps anyone, earlier in the day I tried to run a live CD of 64Studio, also Debian-based, and also got zero touchpad function.  Of course, if all I have to do to finally succeed in switching from windows to linux at this point is go buy myself a cheap usb mouse, i'll probably just forget the stupid touchpad.

---

### Post by NK-Magi on 2008-07-25
Well, I tried most of the settings available in xorg.conf with no changes, and then I found out it wasn't even being recognized at boot, it was saying that it was failing to find the device at x nodes, so obviously the driver isn't leading correctly to the device or the kernel doesn't support it.

What was weird was I got it from my brother and he had it working fine with Fedora Core 5, so I don't know if its the driver version that made it work or the kernel version allowing it to notice the device.

I tried both 32-bit Ubuntu 8.04, 64-bit 8.04, and Fedora Core 9 with no changes in either.

Maybe it was just a weird distant model made by Synaptic that never got stuck in the support pool, never the less, would love to get it working.

If anyone knows how to find the devices and correctly link them to the driver, then I'd really want to hear that info to give it a shot on it again, maybe it'll work.  Thats my best guess from fighting with it.

---

### Post by thomasjw on 2008-07-25
that's good to know, saved me from wasting a lot more time trying stuff that isn't going to work.  i would have been happy just to get the thing to emulate a mouse -- i never wanted to know this much about keyboard shortcuts, argh.  i'm hoping you didn't have to do anything special to get your mouse to work?

---

### Post by NK-Magi on 2008-07-25
Hah after poking at it for a few days I decided to go back to XP but now I'm installing a dual-boot as I'm typing this to give it another go.

From what I've seen, its something along the line of the OS not properly getting the exact location of the touchpad, since (I believe) Synaptic Touchpad drivers are rather generic, if we could properly get the OS headed in the right way towards it, the drivers "should" allow it to work, but I'm not sure, I'm new to linux devices and drivers and such, I mostly know compliling and finding dependencies and such, not hardware work.

Does anyone have any good commands that could get some info for trying to fix this?

---

### Post by thomasjw on 2008-07-25
i'm too much of a n00b to be much help here.  the solution in the case of the nonfunctional HP500 touchpad was to compile a new kernel (see links above), which is also the advice i got from _oOMOo_ in the touchpad thread under the Intrepid Ibex forum.  (I'd put in a link, but without any pointer device that's a lot more difficult!)  If you're doing a new install anyway, it might be worth installing Intrepid just to see if this fix has been included...

is the reason for synclient telling me it can't access shared memory and SHMConfig is disabled, despite my specifically invoking SHMConfig in xorg.conf, that the synaptics driver can't find the hardware and so just doesn't run at all?

---

### Post by NK-Magi on 2008-07-25
I'll try Ibex right now, always worth a shot atleast.

Edit: Weird, its not letting me update to Ibex quite yet, its giving me errors when it trys to get the software sources, so I'm guessing you need to be at 8.04.1 to update.  I'ma give it some time to get the updates done and then I'll give Ibex another shot, if not, I'll download the .iso and try to run it.

---

### Post by NK-Magi on 2008-07-26
Tried Intrepid Ibex, no luck so far, gonna try messing with it some more.

Edit: Tried installing pretty much everything along the lines of synaptics and tried all the combinations with no luck either, I don't know what to try next to hopefully get this to work.

---

### Post by thomasjw on 2008-07-26
wow, you've certainly eliminated a lot of possibilities.  i just gave up on it and bought a cheap usb mouse.  ergonomically better than the touchpad anyway!  (hmm, maybe that is sour grapes.)

---

### Post by NK-Magi on 2008-07-26
Yup, I tried to download some old sources of past drivers around the time Fedora Core 6 was out (when I had the touchpad working with linux) and yet couldnt compile them anyway I tried.  So I'm out of ideas at the moment.

---

