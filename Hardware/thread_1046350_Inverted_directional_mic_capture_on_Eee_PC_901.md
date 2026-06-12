---
title: "Inverted directional mic capture on Eee PC 901"
date: 2009-01-21
forum: Hardware
---

### Post by tamias on 2009-01-21
Hi all,

I'm having a problem with the built-in microphone on my Eee PC 901.

I understand that the stereo microphones at the bottom of the screen are supposed to allow directional recording and noise cancellation, which indeed they do. However, some setting somewhere in the sound driver appears to be inverted, such that the mic picks up sound very clearly on either side of the Eee, and nothing at all from directly in front.

E.g. if I sit and talk to the Eee facing it directly, my voice is not captured (or rather, it is cancelled out by the stereo mic). As I move left and right, to about 45 degrees either side of straight-ahead, my voice becomes clear and is recorded perfectly well.

Searching various forums has thrown up a few terms such as beam forming and echo cancellation, which apparently should be disabled to get the mic input to work correctly. One example is here: [http://forum.eeeuser.com/viewtopic.php?pid=406503](http://forum.eeeuser.com/viewtopic.php?pid=406503) but it relies on Realtek HD Sound Effect Manager on Windows XP.

However my gnome-volume-control (and indeed alsamixer in the terminal) provide only a 'master' level control for the mic input, and no other settings whatsoever apart from 'mute'. There is no mention of any Realtek driver settings.

Can anyone help me to resolve this problem? I'd actually rather like to keep the directional feature if possible, but to reverse the settings so that it records from straight-ahead and cancels out side noise, but if that's not possible it would be nice at least to have all-round audio input and to switch off the noise cancellation!

Many thanks,

Mark

---

### Post by tamias on 2009-01-22
Some further information: I've followed the instructions at [http://www.array.org/ubuntu/snd-hda-intel.html](http://www.array.org/ubuntu/snd-hda-intel.html) and [https://help.ubuntu.com/community/EeePC/Fixes#Microphone](https://help.ubuntu.com/community/EeePC/Fixes#Microphone) but again failed at the first hurdle, as "Front Mic" and "Front Mic Boost" do not exist in my volume control properties.

Additionally, compiling the replacement alsa module (as suggested on the Ubuntu wiki) fails due to missing dependencies. Given that the wiki instructions are for the Eee 900 (and I have a 901), I'm reluctant to poke around too much as I have no guarantee that the replacement module is the correct thing to install, as I think the sound hardware is diferent across the two machines.

---

### Post by ldormon on 2009-02-15
*bump*

I also am have the same issue with 8.10 on an eee 901. Recording on the left or right works but not in the middle. 

How strange :confused:

---

### Post by tamias on 2009-02-16
Thanks for confirming that it's not just me, at least!

I didn't keep Xandros on my Eee for long enough to be able to test that it worked correctly under that OS before I installed Ubuntu, so I still can't confirm whether it's a software (i.e. Ubuntu) or a hardware fault.

Do you have any idea if the internal mic worked correctly with Xandros?

---

### Post by tamias on 2009-02-18
Just to let you know, I've posted a Launchpad bug at [https://bugs.launchpad.net/ubuntu/+bug/331130](https://bugs.launchpad.net/ubuntu/+bug/331130) now that I've confirmed a number of other people are having the same issue.

---

