---
title: "Mouse issue after Karmic Koala upgrade- Left handed not noticed"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Dr J on 2009-11-06
I upgraded to Karmic Koala from the previous version- I use my trackpad left handed- with the buttons reversed.

But no matter what I set in the "Mouse" control panel I get the buttons the "regular" way.

Help please- how do I get my mouse back left handed- my right hand doesn't work all that well, so using the buttons the "regular" way is not possible.

Oh using a Panasonic T4- upgraded and no other issues seen.

---

### Post by xtbt on 2009-11-12
This seems to be a common problem with this release and you are not the only one with the problem. I have that particular problem too. 

I'm using an Acer Aspire 5536 and I can't set the touchpad to left-handed even with a fresh install of Ubuntu.

A thread of this issue were posted some weeks ago but the moderators closed it because 'Karmic Koala' was in development phase. Well, now that Karmic Koala is an Official Release I hope someone help all the lefties users of this wonderful Linux Distribution.

Thanks in advance,
X-TBT a.k.a. The Mentor.

---

### Post by n00pster on 2009-11-18
This below workaround works for me:

=========================================================
Manuel wrote on 2009-11-15:	 #22
temporary workaround:

- run "xinput list"
- Find the name of your touchpad (above the line "Type is TOUCHPAD")
- run xinput set-button-map "<your touchpad name>" 3 2 1
=========================================================

for me it was
xinput set-button-map "SynPS/2 Synaptics TouchPad" 3 2 1

May be we can add this to our .bashrc

---

### Post by xtbt on 2009-11-19
> **n00pster said:**
> This below workaround works for me:

=========================================================
Manuel wrote on 2009-11-15:     #22
temporary workaround:

- run "xinput list"
- Find the name of your touchpad (above the line "Type is TOUCHPAD")
- run xinput set-button-map "<your touchpad name>" 3 2 1
=========================================================

for me it was
xinput set-button-map "SynPS/2 Synaptics TouchPad" 3 2 1

May be we can add this to our .bashrc

OMG, you're my life saver. I was thinking that maybe I was gonna live with the problem forever. It's a really pain in the *** for lefties like me having to use a touchpad with the right hand.

About putting the script in .bashrc, I don't think that would be the best place to put it. I suggest adding the entry into the Start up applications list.

Well n00pster, thank you very much.
X-TBT a.k.a. The Mentor.

---

