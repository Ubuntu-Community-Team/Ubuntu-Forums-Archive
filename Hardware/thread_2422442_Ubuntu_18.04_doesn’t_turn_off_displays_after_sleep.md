---
title: "Ubuntu 18.04 doesn’t turn off displays after sleep"
date: 2019-07-07
forum: Hardware
---

### Post by KemKin on 2019-07-07
My setup is using original nvidia drivers and 1080 gtx connected to two 4K Dell (U2718Q) monitors.

If I configure power management of both monitors through xset, then I can turn off ether of them and both of them will be correctly turned off.

However, whenever I put my Ubuntu to sleep, both monitors would correctly show that they both have lost signal, then turn off their backlights.

In a few next monents comes the unexpected: sometimes, either one of them or both, will turn on their backlights and keep showing this empty, supposedly black image (no “no signal” is shown). Imagine an LCD screen with full backlight but only a black image is rendered?

I have already tried xset’ing them to be off before putting my computer to sleep with no luck.

Any ideas which of the components may be responsible for it?

---

### Post by fragglebliss on 2019-07-07
I can't offer you a solution for your problem other than recommend you stop using sleep, as it's a problem I've experienced before with Ubuntu (and other Linux distributions too). I've become a staunch traditionalist and avoid modern system modes like sleep and hibernation. Now, I simply use traditional methods of boot/powerup. That way, you avoid all problems and don't experience any of this crap.

Sorry I couldn't offer any further help. But do think about just powering off the system in the future. And you'll get a much cleaner system upon fresh boot too and no possibility of orphan processes lurking in the background.

---

### Post by KemKin on 2019-07-08
> **fragglebliss said:**
> I can't offer you a solution for your problem other than recommend you stop using sleep, as it's a problem I've experienced before with Ubuntu (and other Linux distributions too). I've become a staunch traditionalist and avoid modern system modes like sleep and hibernation. Now, I simply use traditional methods of boot/powerup. That way, you avoid all problems and don't experience any of this crap.

Sorry I couldn't offer any further help. But do think about just powering off the system in the future. And you'll get a much cleaner system upon fresh boot too and no possibility of orphan processes lurking in the background.

You're saying "it's a problem you've experienced before" - do you mean in general, you have experienced the monitors not being turned off?

---

### Post by fragglebliss on 2019-07-10
Yes, that's correct.

---

### Post by him610 on 2019-07-10
It is not an Ubuntu issue; the application does what it is supposed to, terminates signal to monitor; however, the monitor has sensor that detects the loss of signal and displays message to that effect. Recommended workaround, don't be afraid to use monitor On/Off switch.

---

