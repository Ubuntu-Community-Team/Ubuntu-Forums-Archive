---
title: "Audigy2 ZS Notebook Line-in Recording?"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by Thor Harald Johansen on 2007-03-31
Hello folks,

I have an Audigy2 ZS Notebook PCMCIA card that's working wonderfully under Ubuntu Feisty, but line-in recording is a different story. It failed to work on 1.0.12 and 1.0.14rc3, even after hours of googling and playing around with Playback/Capture sliders/switches in the alsamixer.

So I got the RSYNC versions of alsa-driver/alsa-libs/alsa-utils, compiled and installed them successfully. I am dual-booting this laptop with Windows XP on the other partition and it was rumored that line-in support on the A2ZSN was finally coming to Eugene Gavrilov's kX Project Driver for Windows. Eugene claims to have used new ALSA code as a reference to implement this. I have this new driver running on the Windows XP partition and it does indeed work. How strange it is then that I can't seem to record a peep using ALSA on Linux...

[color=red]I've written plenty of C and Java code. I've written assembly programs for PIC microcontollers, the emu10k1 and even x86. I'd be happy to help debug the driver. I'm going to hang out in the #lad IRC channel on FreeNode as THJ for the next days, so if anybody's interested...?[/color]

---

### Post by xilef on 2007-04-18
Hi,

I have the same exact problem over here and I would like to help solving it. I am a professionnal programmer too and I'll be happy if I could give a hand. I will idle on *#lag* as well as **xilef___**.

Regards

---

### Post by rmfought on 2007-05-03
Seems this bug is still open over at the [ALSA bugtracker]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2058#bugnotes")

Add some feedback maybe we can get some attention brought to it.

---

### Post by jawrat on 2007-06-15
Has anyone found a possible solution to this issue?  i'd really like to be able to use ubustu/ardour to record in something better than mono.  

Thanks,
j

---

