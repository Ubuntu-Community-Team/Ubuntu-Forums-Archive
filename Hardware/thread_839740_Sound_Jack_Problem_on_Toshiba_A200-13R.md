---
title: "Sound Jack Problem on Toshiba A200-13R"
date: 2008-06-24
forum: Hardware
---

### Post by nabilgh on 2008-06-24
hi...I am using a Toshiba Satellite A 200 13r I have installed Hardy 8.04 and am having problems with my sound output. Sound works on both my laptop and headphones at the same time. what should i do to mute the laptop speakers when i am using the headphones. Thanks

---

### Post by phidia on 2008-06-24
I wanted to know the answer to that myself. I found [this thread]("http://ubuntuforums.org/showthread.php?t=798945&highlight=mute+main+speakers") at the multimedia forums try that and let us know how it works.

I did more searching on this and the answer seems to be installing the latest version of alsa.
There's an old thread on doing that [here]("http://ubuntuforums.org/showthread.php?t=455147").
Anyone following that would need to use the latest alsa releases but the method/steps should be good.
I'll probably try that later and see how it goes.

---

### Post by nabilgh on 2008-06-25
Well i tried the first solution it didn't work coz there's no alsa-base file in the /etc/modprobe.d directory. So i tried the second solution in [http://ubuntuforums.org/showthread.php?t=455147&page=1](http://ubuntuforums.org/showthread.php?t=455147&page=1) and installed all the alsa drivers but the speakers still don't mute when i plug in the headphones, but the sound volume became higher than before and that's good.. thanks for the help

---

### Post by phidia on 2008-06-25
I think you need to install the 4 packages from the asla site (alsa-driver, alsa-lib, alsa-util & alsa-firmware) when you get those installed per the instructions then open volume control and you should have and option to select sound sense which gets you the muting of the main speakers when the headphones are plugged in.

---

### Post by nabilgh on 2008-06-25
well i installed all the alsa drivers and followed all the instructions but i didn't find this option in the volume control to mute the speakers. There's the headphones option in "Switches" i can enable or disable the headphones but the speakers still dont mute.

---

### Post by erani on 2009-01-09
Somewhere I found that must add to alsa-base file a codec option
So I add
options hda-codec-realtek
in /etc/modprobe.d/alsa-base

I found it here [http://ubuntuforums.org/showthread.php?t=908996](http://ubuntuforums.org/showthread.php?t=908996)

---

### Post by dveej on 2009-04-20
Hi, Erani. Thanks for doing this legwork on this. 
I have a suggestion (for you and for everybody, actually, especially including the "armin-kraiton" person who looks like s/he wrote the wiki page you linked to - although there is no way to tell or to contact whoever wrote it...): 

When you are posting something that we newbs should add to the terminal, please write out the command in full. Some of us don't understand how to properly type in something like:

/etc/modprobe.d/alsa-base



For example, I myself don't understand the proper form of this command. It doesn't work when I paste it into my terminal as it is written. I will now have to spend hours angrily searching for an example of this command written out fully. I suspect there is something about "sudo" or something that must be added, and I have experimented a couple of times but to no avail. I must also add that because this knowledge is so basic, and because there are several instances of users with this problem in the forums, I will get ignored or even slammed if I simply ask for someone to help me directly, rather than scouring the forums for every single instance of attempts to solve this problem.

I realize that this is very basic knowledge, and sorry if I'm boring the cool experts with this; but really listing the full command can only help the Linux cause!

Thanks for helping with this.

---

