---
title: "Where did all the sound go?"
date: 2009-01-03
forum: Hardware
---

### Post by djhvt on 2009-01-03
So im using Hardy on a Everex Gbook (also known a stepnote) and thanks to the joy that is flac my tunes sound awesome even on my crappy laptop speakers. But to my horror i came across a problem i didnt previously have while on a long train ride (of course): When i plug my headphones into my computer i get no sound in them.

For your consideration:
*my headphones work in my ipod no issue
*my friends headphones which are a completely different model/brand dont work either in my laptop
*And, my headphones used to work in my laptop. this is new.

Any ideas? Thanks so much in advance!

---

### Post by Paul Miller on 2009-01-04
Do you get any sound out of the speakers when you are not using headphones?

The first thing I would try to fix this is to do 
```

apt-get purge alsa-*

```
and then reinstall alsa.  Don't ask me why, but this worked to fix the sound on my machine one day when it just stopped playing.

---

### Post by gettinoriginal on 2009-01-04
These sites are helpful in solving sound problems:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by djhvt on 2009-01-05
the first suggestion did not work at all, and it would appear the second suggestion my give some clues. My VIA VT1708A audio card is not listed as compatible with alsa, and there for there are no drivers for it. So i guess its by shear luck that my speakers work. Ive down loaded 8.10 to see if the live cd offers any solutions. 

 What confuses me is that it did work under 8.04 for the last few months that ive had it. It also worked under Gos when i first got it. Also this model from everex seem popular to use with ubuntu derivatives such as Gos and Zombu. Is there anyone else that has run into this issue or has a solution please let me know.

again i thank eveyone for the help!

---

### Post by Lee_Machine on 2009-01-05
If it did work and now does not this can mean a few things.

One hardware regression: For some reason hardware drivers are either removed, or broken for some models. To fix this go into symaptic and install hardy backport modules. For 8.10 it would be intrepid.


Another thing is the sound for output can be turned off. In gnome there will be a sound icon on the top right. Make sure everything is turned up.

You can also try this in terminal:

sudo gstreamer-properties

Make sure under the audio tab the sound architecture you are using is selected. i.e. paulseaudio, OSS, ALSA. 

I personally use paulseaudio for everything.

Do the same thing as a non sudo user to make sure they match.

Does that make since? They should as sudo is for global configurations.

Did trying the Live-CD of Ibex work?

---

### Post by smudger86 on 2009-11-25
I also have VIA VT1708A sound card and when i updated from Jaunty to Karmic my sound disappeared, i usually get my sound through the TV speakers as soon as i activate Twinview, now nothing happens. When i look at System > Preferences > Sound > Hardware no devices show up on the list. I have not installed any sound drivers as i did not need to when i used jaunty 9.04. I've tryed to find a driver, but I'm not really sure what to look for..

Ps. i have only been using linux for a few months(after about 15 years of windows) so i am quite clueless of how things work here. All tips appreciated :) 

specs follow:
Ubuntu 9.10 (karmic)
Kernell: 2.6.28-15-generic (#52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009)
GNOME: 2.28.1 (Ubuntu 2009-11-03)
Sound card: VIA VT1708A
Graffics: GeForce 7300 SE/7200 GS
CPU: Intel(R) Pentium(R) D CPU 3.00GHz

---

### Post by jmac32here on 2009-11-27
I noticed on my Everex N Series laptop that a headphone option was not on either of these lists.

However, I did find a fix in the preferences.

First you need to set the preferences to display "Duplicate Front" on the Switches tab.

Once that is done, you can activate Duplicate Front and your headphone jack will work as though it is the main speaker.

---

