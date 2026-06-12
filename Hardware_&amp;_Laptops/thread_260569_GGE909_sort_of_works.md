---
title: "GGE909 sort of works"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by argash on 2006-09-18
I have a GGE909 gamepad that will work in jscalibrate but wont work in zsnes or gsnes9x.  Any ideas?

---

### Post by argash on 2006-09-19
update: I now have the buttons working in both zsnes and gsnes9x but the d-pad and analog sticks are still unrecognized in both programs (though they work fine in jscalibrate as mentioned above)

---

### Post by TrueJk7 on 2006-10-26
Hey I've got the same thing from walmart. lol, I got the last one too.

I found on another forum [http://forums.debian.net/viewtopic.php?t=8729&sid=012bf16daaeee5ad3cb1b4825999bdd3](http://forums.debian.net/viewtopic.php?t=8729&sid=012bf16daaeee5ad3cb1b4825999bdd3)

And followed it though to get mine to work. It was recognized in Joystick Calibrator but not in the programs I wanted to use it in so before I launched an application to use it in I ran in terminal

```
sudo rmmod joydev
sudo modprobe joydev
```

and it works perfectly right now. Kinda cool that Linux had the drivers for this thing, eh? only if we could get that escape button to work right!

Peace bro. Hope this helps

---

### Post by tophatandy on 2006-12-31
got the exact same thing..

cant seem to get it to work (at all) on Edgy.

is there like an app I need to download or something to get this to work..
do I need to run the cd that came with it in wine or something? ...
how did you guys do it?

---

### Post by tamdar on 2007-01-28
Hey folks , just picked up one these to try in some 1st person shooter type games, and they're not compatible. any ideas on games of this type that it will work on?

---

### Post by KeepAwayFromChildren on 2007-07-02
I'm having this problem too. FCEU and ZSNES both recognize the buttons, but not any of the joystick axes. My guess is that the program expects input as some form of digital input, while the axis claims to be an analog stick (even the two for the d-pad). Is there some way to say "this is not an analog stick, this is a set of buttons"?

---

