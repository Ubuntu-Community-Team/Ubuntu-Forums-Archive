---
title: "Alienware 15 Headphones"
date: 2016-03-10
forum: Hardware
---

### Post by lucas-oskorep on 2016-03-10
Hi There so I have an Alienware 15 R1 (2015) laptop and i am currently running gnome ubuntu 15.10 and i am having a bit of difficulties with the soundcard.  Currently in alsamixer it appears as if the sound card is recognized correctly, and it has all of the features it normally does, however there are two categories for  HP/speaker and HP/speaker - auto detect that are currently in an off state and no matter what i have tried to do with plugging in headphones to my laptop, they will not turn on.  To be honest i'm not really sure where i need to go next and some guidance would be appreciated.  Thanks.

---

### Post by rtorres4 on 2016-03-19
Bumping this up. I have the same laptop and I am running into the same issue as the user above. Could we get a reply from someone please.

---

### Post by rtorres4 on 2016-03-27
Bumping. Cannot solve this issue :(

---

### Post by tony116 on 2016-03-28
Bumping, I have the same laptop, Alienware 15 R2, and cannot get headphones to output sound. 

The codecs are being detected as: Card#0 Creative CA0132 and Card#2 Intel Skylake HDMI

The sound works just not when headphones are connected, IE sound still plays from laptop speakers. To clarify this laptop has two audio jacks, 1 MIC input and 1 dual type jack which can accept headphones or headset. The audio card is classified as a Creative Recon 3Di by Alienware. Please anyone with recommendations would be huge help!

---

### Post by mörgæs on 2016-03-28
How does 16.04  (development version) work?

---

### Post by rtorres4 on 2016-03-28
I installed Ubuntu Gnome 16.04 about a week ago and it didn't fix the issue. Can we get maybe a nod from the maintainers of Alsamixer (or any sound driver wizard), we could really use some help over here. I'm willing to provide any data and try anything to get this to work.

---

### Post by QIII on 2016-03-28
Developers don't generally hang out here unless they stumble in by mistake.  The Forums are not a good place to get their attention or support.

---

### Post by rtorres4 on 2016-03-28
What's the best way to get a fix for the guys with an Alienware 15 R2 who want to get their headphones working? Should we submit something to the canonical directly or go to the alsamixer mailing list and ask there?

---

### Post by mörgæs on 2016-03-29
You could discuss it with the people in the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427") and after that open a [bug report]("http://ubuntuforums.org/showthread.php?t=1011078").

---

### Post by Yellow Pasque on 2016-03-29
So have you folks tried turning on headphone auto-detect in alsamixer? Use spacebar to toggle binary controls in alsamixer. Use up/down arrows to alter controls with multiple setttings. Use 'm' to mute/unmute things.

These links could be relevant. I'm not sure if they're the exact same model or not (as I find Alienware model naming very confusing).

[https://github.com/torvalds/linux/commit/fe14f39e88c8ac16d0a051f8444a2294f8cb358c](https://github.com/torvalds/linux/commit/fe14f39e88c8ac16d0a051f8444a2294f8cb358c)
[https://bugzilla.kernel.org/show_bug.cgi?id=101981](https://bugzilla.kernel.org/show_bug.cgi?id=101981)

---

