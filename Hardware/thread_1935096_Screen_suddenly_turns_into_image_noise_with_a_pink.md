---
title: "Screen suddenly turns into image noise with a pink horizontal bar before fading away"
date: 2012-03-03
forum: Hardware
---

### Post by Svip on 2012-03-03
I left my laptop for 20 minutes, in the mean time Ubuntu decided to turn off my screen (which I expect it to do), but when I returned and powered on the screen again, it was just like an image of noise with a thick pink bar to the right side of the screen.

The noise then began to fade away as frost on a window that is heating up, before only remaining in the side, while the pink bar remained in view.

Regardless of my keystrokes, nothing happened.  Going to TTY1 or 2 did not work.

So I rebooted, assuming a hiccup.  But as *soon* as a selected Ubuntu from the boot manager, the same visual strangeness occurred.

I feared there was something wrong with my laptop screen, but Windows 7 runs without problems.  I know X cannot toggle between two graphics cards, but surely it should be able to select one or something?

It's a Dell Precision M4600 and Ubuntu 11.10 using Unity (although its failure before X even is started (I assume[1]) makes me wonder whether Unity has anything to do with it).

[1] I don't know what sort of hack Ubuntu uses to make the start up loading screen.

---

### Post by LinuxFan999 on 2012-03-03
Can you upload a picture of the problem?

---

### Post by Svip on 2012-03-03
Well, will you believe it, now Ubuntu works again.  However, should the problem resurface again, I will be sure to make a picture.

---

### Post by Svip on 2012-03-05
That was a short run.  The problem has re-surfaced, and unlike before, where I simply had to leave the machine turned off for a while or boot into Windows for a while, and then back into Ubuntu, the problem persists when I enter Ubuntu.

Because I cannot interact with the system, I cannot produce a screenshot, and while my Nokia N900 *does* have a camera, it has decided to be an incredible prick and not let me access my MicroSD card (and when I take it out, it won't save to the phone's main disk).

So I cannot show you a picture of what it looks like.

It generally starts as a completely white screen and then it retreats except for the pink bar.  Although in some cases the pink bar is entirely missing.

I am still at lost to *why* it happens.  Oh and, just for the record, I installed Ubuntu via the Windows Installer.

---

### Post by azertyfred on 2012-05-13
same here, yesterday my screen turned into a pink purple party with a lot of noise (visual noise). The background of thunderbird and other programs became very colourful. After graphic restart it was back ok. This mornig (day after) I get a little bit of noise on my screen and now it's gone again. very strange..hope it's not a hardware problem.

---

### Post by Svip on 2012-05-13
I discovered that my problem is related to my laptop having Nvidia Optimus.  I can turn it off, but then everything becomes incredible slow and low resolution.

It is much more fruitful to bet on it just working or you have to reboot a couple of times.

---

### Post by azertyfred on 2012-05-14
I don't have nvidia, I have ATI Radeon. But it seems to happen when the fan blows harder. When I push a certain spot on my laptop, the noise dissapears..very strange.

---

### Post by Amraks on 2012-05-14
Screen Artifacts.

Sounds like your GPU needs a reball.

What actually happens is the solder balls on the gpu get hot and do not make contact with the motherboard of the laptop.

These images you are seeing are called artifacts.

Look them up on youtube.

---

### Post by azertyfred on 2012-11-06
Hi, just to let you know, my laptop is under guarantee so I let it fixed by HP, I think they changed the LCD cable and now it's OK.

---

