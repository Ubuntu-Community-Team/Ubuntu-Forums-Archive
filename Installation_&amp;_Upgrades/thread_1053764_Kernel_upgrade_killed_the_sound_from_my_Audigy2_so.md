---
title: "Kernel upgrade killed the sound from my Audigy2 sound card."
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by lotharjade on 2009-01-29
I just got the new kernel upgrade via the update manager.  It seems to have killed the sound in my system.  I have a Creative Audigy 2 ZS [SB0350] sound card.  When I go to System -> Prefences -> Sound, and try to test the sound playback for my card (under sound events) it doesn't do anything no matter what I try.

What went wrong and how do I fix it?

---

### Post by Crafty Kisses on 2009-01-29
Have you tried to see if the volumes are correct in alsa?

---

### Post by lotharjade on 2009-01-29
Um... No.  I don't think so.  How do I do that?

---

### Post by Crafty Kisses on 2009-01-29
Run this command in Terminal:
```
alsamixer
```

---

### Post by vanadium on 2009-01-29
See here: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179)
They changed a setting apparently, that you can change back.

---

### Post by mclode on 2009-01-29
I am having exactly the same problem: no sound from my "Audigy 2 ZS [SB0350]" with kernel 2.6.27-11.

I have gone back to 2.6.27-9 and the sound is fine. As far as I can see the volume settings are not changed when I boot 2.6.27-11.

Cheers,

Martin.

---

### Post by mclode on 2009-01-29
That works for me :D
Ubuntu version of the solution:
Right-click on the Volume icon and choose _O_pen Volume Control
Click on _P_references
Scroll down to and check "Audigy Analog/Digital Output Jack" then _C_lose
On the Swithces tab, un-check "Audigy Analog/Digital Output Jack".

---

### Post by lotharjade on 2009-01-29
I can confirm what you are saying mclode, going back to the 2.6.27-9 fixed my problems.  Hopefully they fix what is wrong in this kernel.  

I will further test your suggestions.

---

### Post by lotharjade on 2009-01-29
> **mclode said:**
> That works for me :D
Ubuntu version of the solution:
Right-click on the Volume icon and choose _O_pen Volume Control
Click on _P_references
Scroll down to and check "Audigy Analog/Digital Output Jack" then _C_lose
On the Swithces tab, un-check "Audigy Analog/Digital Output Jack".

Ok, I roughly followed this and it solved my problems.  I did have one slight variation on your suggestion.

First I was in the 2.6.27-9 kernel when I saw your suggestions so I looked at what you were suggesting with the volume control before I switched back over, which is important later.

[LIST=1]
[*]Right-click on the Volumn icon and choose "Open Volume Control"
[*]Open the switches tab
[*]un-check "Audigy Analog/Digital Output Jack"
[/LIST]

My first note is that checking the "Audigy Analog/Digital Output Jack" button was not necessary as mine was already checked.

Lastly, unchecking the "Audigy Analog/Digital Output Jack" bit in the switches tab is the exact opposite as to how it is set up in the previous kernel.  

Regardless, SUCCESS!!!  \\:D/ =D> :biggrin:

---

### Post by mclode on 2009-01-30
I think I cleared out most of my switches when I had a clear out a while ago. It might have been when I found out that you have to check the Tone switch to make the Bass and Treble controls work.

I suppose it is worth keeping the switch there now, in case we have to switch it back in a later release ;)

---

### Post by lotharjade on 2009-01-30
I am surprised they aren't doing a quick fix to this problem.  There is a bug report, and it seems everyone knows what the problem is.  One would thinkt this would be a quickie programming fix for people who do this sort of thing.  

Most other problems I see don't have the benefit of having any idea what is causing the problem.  My monitor hdmi issues come to mind.  LOL.

---

### Post by sfehrman on 2009-02-14
Thanks for the help!
I can confirm that unchecking the Audigy Analog/Digital Output Jack fixed the problem.

---

### Post by Emre Çelikten on 2009-04-01
No, actually this leads to another problem.

I don't know about you, but there is bit depth reduction in the sound in my system after applying the workaround. I can hear some artifacts in the sound which are like bitcrushing effects.

Any fixes to this issue?

Thanks in advance.

---

