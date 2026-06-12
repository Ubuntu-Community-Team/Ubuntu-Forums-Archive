---
title: "no sound when earphones plugged in 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by deb0and on 2009-10-30
Hello

I have an amilo li1705 laptop, I have tried everything to get my headphones working in ubuntu 9.04 and i was hoping things might have changed when i upgraded to 9.10 but it hasn't

Sound works perfectly until earphones are plugged in, sounds stops from speakers but doesn't come through earphones.  (not faulty earphones either)

I have a vt1708/A card.  Also there are even less options to choose from in the new sound control panel.

Does anyone know how to get my earphones working?  This has been driving me mad for years.

---

### Post by Vaphell on 2009-10-31
true that - extremely annoying issue with fs amilo 1705.

it was possible to get it working in 8.04 (i managed to do that) by patching 1 file and compiling alsa, i've seen people claiming to have vt1708 working in 8.10/9.04  but there are no tutorials how to achieve desired effect in 9.10.
And why on earth hasn't this issue been resolved in alsa if there was a working solution about 2 years ago? :/

---

### Post by deb0and on 2009-11-01
Yes you are right...... that is the reason i have upgraded to 9.10 in hopes that it would have been sorted.  As you say 2 years have past but still no solution, pretty appalling really!!!  I am now searching around the web looking for another distro which works with my sound card as i can't do without earphones, I have even contemplated going back to Windows :twisted:, but i would rather not.

I am really frustrated, something so simple...........

---

### Post by Vaphell on 2009-11-03
consider reverting to older version of ubuntu (8.04 being the easiest) - a little bit of manual labor and you get both 3d/compiz (for exactly one version of kernel) and headphone jack working.
Unfortunately collective wisdom of users hasn't produced any solutions to the problem for karmic yet - I scan ubuntuforums/launchpad/alsa website/google regularly.

I doubt you'll find a distro working ootb, after all you have to patch stock alsa to get sound configured properly on these shitty amilos.

---

### Post by jflassche on 2009-11-12
Hi,

I managed to get the sound working on 9.04 and am currently trying to get it working on 9.10.
The trick (so it seems) is to use ALSA 1.0.19 instead of a newer version.
There's a great tutorial on getting it to work on 8.04 that actually works on 9.04. ([http://ubuntuforums.org/showthread.php?t=1124185](http://ubuntuforums.org/showthread.php?t=1124185))

I'll keep you posted.

Sincerely yours,
Jeroen.

---

### Post by jflassche on 2009-11-12
It works! At least for me...

What I did is:

[LIST]
[*]download and extract alsa-driver-1.0.21
[*]patch alsa-driver-1.0.21/alsa-kernel/pci/hda/patch_via.c (see link in previous post)
[/LIST]

And...

```

sudo apt-get install linux-backports-modules-alsa-karmic-generic
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
make
sudo make install

```

After reboot open mixer window and disable independent HP.

Sincerely yours,
Jeroen.


(edit: typo)

---

### Post by jflassche on 2009-11-13
Just noticed that I only hear the left channel when using the earphones, without them both channels work...

Sincerely yours,
Jeroen.


edit:
[shame]mixing pannel, channel panned totally left...[/shame]

---

### Post by tzotzolyno on 2009-11-15
> **jflassche said:**
> Hi,

I managed to get the sound working on 9.04 and am currently trying to get it working on 9.10.
The trick (so it seems) is to use ALSA 1.0.19 instead of a newer version.


Hello, Jeroen. Do we need suplimentary steps for recompiling ALSA 1.0.19 for 9.04, or simply the same steps from the 8.04 tutorial?

I ask you for 9.04 because of the video driver. I saw that Via Linux Portal has posted the stabile driver for 9.04 (and I home it works.

Many thanks!

---

### Post by jflassche on 2009-11-15
Hi tzotzolyno,

I followed the steps described on this forum here:
[http://ubuntuforums.org/showthread.php?t=556217](http://ubuntuforums.org/showthread.php?t=556217)

Just compile the alsa-driver with the sound card and kernel headers specified:
```
./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
```

---

### Post by Vaphell on 2009-11-26
thanks jflassche, i'll try that as soon as i have access to the troublesome machine.
i hope it'll work finally :D

---

### Post by tzotzolyno on 2010-01-13
> **Vaphell said:**
> thanks jflassche, i'll try that as soon as i have access to the troublesome machine.
i hope it'll work finally :D

So, have someone solved the sound problem in Karmic Koala? Now, I don't use Ubuntu on my Amilo Li 1705 but I really wanna install it on this notebook too.
Please, if somebody find a solution, leave here indications to be followed even by the beginners.
Thanks with anticipation!

---

### Post by Vaphell on 2010-02-16
jflassche's info is accurate, i made headphones to work
i had other problems though, probably because of pulseaudio - volume slider mutes itself very often which is annoying.

---

