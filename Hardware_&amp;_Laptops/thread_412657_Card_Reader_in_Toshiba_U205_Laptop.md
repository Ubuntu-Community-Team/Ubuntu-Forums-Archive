---
title: "Card Reader in Toshiba U205 Laptop"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by pjssilva on 2007-04-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/53923) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I got a new Toshiba U205-S5067 laptop. Almost everything works well. But the card reader does not work. This is certainly related to the bug linked above.

Is there any other owner of a U205 laptop? Did you manage to get the card reader working?

Obs: I tried the setpci trick and it seems not work with this laptop.

---

### Post by quickwitt on 2007-05-26
Same laptop. Same issue.

---

### Post by exkova on 2007-08-10
I got almost the same model (s5057 instead of s5067) and the same problem. 

Everything was working out of the box with feisty except for:
- screen resolution: had to apt-get the right driver for xorg;
- fingerprint: had to install thinkfinger and add uinput to /etc/modules
- card reader: well, you guys know....

It actually worked a couple of times but in a completely random fashion (logs don't show any difference from either way, except that when it works you can see a mmc block device spawning into existence) but even when it doesn't work you can still see the sdhci module message saying everything is alright (supposedly) .

Even though I'm not an Ubuntu guru, I've been in and out of  Linux for a long time and the only explanation I have for this is: **bad driver** (or module if you wish). The hardware itself is not broken (works flawlessly under you know what OS!). The hacks and workarounds proposed on the bug thread above just works for some people because the hardware might be a little different (like different firmware versions or something like this), even with the exact same models of laptop.

Nothing to be done here guys except wait for the next kernel and pray!

---

### Post by Joe Eckner on 2007-10-29
same here but 7.10 didn't help either
I am not expert also, couldnt we get some help here?

---

