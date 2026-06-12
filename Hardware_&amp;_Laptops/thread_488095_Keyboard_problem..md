---
title: "Keyboard problem."
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by LocoMan on 2007-06-29
I'm having a weird keyboard problem and nothing I've tried has worked so far.

Basically I just can't get key repeat to work properly. When I repeatedly press a button very fast, instead of getting that key typed fast, I get like 2 or 3 letters typed, then a pause, then a very fast burst of letters, which isn't really a problem for regular typing (I don't type THAT fast), but isn't really usable on games like MAME arcade games that require very fast repeated presses of a single key (like an attack key).

I have an athlon 64 XP, no dual cores or anything, nvidia 6600 video card and a simple non fancy keyboard, and I'm running feisty.

I've tried everything google has turned up (noapic, notsc and a couple others I don't remember right now added to grub), and so far no idea

BTW, while I've been using linux for a few month, I'm still very newbyish on the internals, so any sugestion, I'd like you to tell me how to do it or how to check it.

---

### Post by LocoMan on 2007-07-04
I usually don't like to do this on forums... but... bump.

Any ideas?

---

### Post by McBrain on 2007-07-04
Same problem here!

I just got a new computer, on the old one it was working perfectly fine! Your config proofs that one of my theories os wrong! I thought it  is the chip set support!

My config:

Intel P965 based board (Core2 E6600)
Logitech Keyboard connected via USB

I think, it is the USB support! My BIOS know one option, where I can choose how the USB keyboard is supported: Via BIOS or OS. When controlled by BIOS, I have the described problem, if set to OS it is working.
But unfortunately I can not use my keyboard in boot menu, which is not acceptable!

I some other forum I found a thread on this, but also with solution:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63024)

Regards
McBrain

---

### Post by McBrain on 2007-07-04
Forgotten to mention I am using Kubuntu 7.04 (up2date, just updated)

---

### Post by McBrain on 2007-07-09
Not a solution but a root cause:

In my case, when ever I have the problem and do a warm start afterwards and do a memtest, it fails! In my case this is a very particular problem, because memtest does not fail when I do a cold start. Whether then the problem also does not occur, I still need to prove..having now some other problem.

So in case you have this problem, check your memory!

---

