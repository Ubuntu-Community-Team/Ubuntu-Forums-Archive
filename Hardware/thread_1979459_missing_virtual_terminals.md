---
title: "missing virtual terminals"
date: 2012-05-13
forum: Hardware
---

### Post by urlwolf on 2012-05-13
My HP 8540w has spotty 'resume' (from memory).
That is, 80% of the time, it'd come back, the rest it'll just show a blank screen. In the linux world, this is sort of expected for a laptop. This is how bad things are.

But I suspect it's an X crash. If I could at least get to a terminal, I could restart X.

What I've found is that I have no virtual terminals (!).
That is, ctrl alt F1-F7 does nothing!

This is very serious. I'm running KDE and the proprietary nvidia drivers. But I don't think that matters much.

Where would you start debugging?
Thanks

---

### Post by steeldriver on 2012-05-13
> **urlwolf said:**
> 
But I suspect it's an X crash. If I could at least get to a terminal, I could restart X.

What I've found is that I have no virtual terminals (!).
That is, ctrl alt F1-F7 does nothing!


doesn't that rather suggest it's *not* an X crash?

I am in a somewhat similar situation with an old Thinkpad - it turns out in my case that *everything* is resuming (including the X session and applications) but the LCD backlight is just not switching on, so *all* TTYs are dark

I can confirm this by SSH'ing into it - or in fact if I connect an external VGA monitor - those are the 2 first things I'd try

---

### Post by markbl on 2012-05-13
The proprietary nvidia driver on 12.04 has a few bugs, for some hardware. E.g. for me current + beta versions crash frequently and also virtual terminals don't work at all. See my comment here [https://bugs.launchpad.net/unity/+bug/982485/comments/136](https://bugs.launchpad.net/unity/+bug/982485/comments/136).

I am now using the open nouveau driver and all is well, including virtual terminals.

---

### Post by urlwolf on 2012-05-15
> **markbl said:**
> The proprietary nvidia driver on 12.04 has a few bugs, for some hardware. E.g. for me current + beta versions crash frequently and also virtual terminals don't work at all. See my comment here [https://bugs.launchpad.net/unity/+bug/982485/comments/136](https://bugs.launchpad.net/unity/+bug/982485/comments/136).

I am now using the open nouveau driver and all is well, including virtual terminals.

Thanks, 
I'll try that. I moved to proprietary because with noveau I had plenty of crashes too.
What a pain, there's not a single distro in 10 years that has worked 100% with ANY hardware.
Now I cannot get the keyboard to work when resuming. Bah!
UPDATE: tried noveau. VTs are still gone. Maybe this is kde?
noveau couldn't even get the correct native resolution of the laptop screen, and didn't even see the external monitor. Had to go back to nvidia. Well, this is not the quality I was expecting for a LTS...

---

### Post by urlwolf on 2012-05-16
Doesn't seem to be kde.
At least one other kde distro doesn't have this problem (sabayon).

---

### Post by CraigPid on 2012-12-13
I realize that this is an old post but no one really seems to have any sound advice on this issue that I've found.The most simple obvious explanation....do you have a keyboard that has other actions available for the F keys?Is there an F Lock button?

---

### Post by steeldriver on 2012-12-13
Welcome - yes it is a rather old post

FWIW on my nvidia based laptop (not the one I posted about earlier in the thread) I found that I had to 'unblacklist' the nvidia framebuffer device to get *my* VTs to display

---

### Post by markbl on 2012-12-13
Back at the time I posted about this it was due to a bug in the nvidia driver. However, recent nvidia versions are ok (since v302.*?).

---

### Post by s_raiguel on 2013-01-29
Same problem. Ever since I got my new system, with an Nvidia GForce GTX 650 Ti, no virtual terminals with ctrl-alt-Fn, just a black screen with a blinking cursor. The TTY processess are running, and it's not a problem with the supported video modes in grub.conf, as some have suggested. Nor is it strictly a hardware problem, since a previous distro running on an old drive still gives normal access to the terminals. I suspect the difference is due to the newer Nvidia drivers on the current system, but so far, efforts to install that older Nvidia driver on the current system have not been successful

The terminal is in fact, there and running- it's simply not displaying anything but the blinking cursor. I discovered that if I log in "blind" and enter a command, such as "restart", it carries out that command. 

Today, however, I made a curious discovery, which may be a clue, and at the very least constitutes a workaround: If I first boot into recovery mode, then select "resume", then when the GUI comes up, I can get the terminal, with it's login prompt displayed as it's supposed to be. Seems to me that some aspect of the display is being initialized by the recovery console that is skipped or not being given enough time to respone during a normal boot.

---

