---
title: "hp G60 Microphone vs Speakers Dilemma"
date: 2010-08-04
forum: Hardware
---

### Post by Ben2r25 on 2010-08-04
I'm working on a friend's HP G60-630 US laptop. It's running Ubuntu 10.04 32-bit. At first headphones weren't working with the computer so I installed the Linux-backports-modules-alsa-lucid-generic package and added this line:
```
options snd-hda-intel model=dell-vostro
```
to /etc/modprobe.d/alsa-base.conf. 

The internal mic also did not work. Adding the line:
```
options snd-hda-intel position_fix=0 enable=yes
```
to alsa-base and choosing mic f in GNOME Alsa mixer fixed this issue. However, those two lines don't play nicely with each other; when both of the lines are in the file the headphones work properly but the mic does not. So, at this point, I can either have working headphones or a working mic, but not both. Anyone know how to fix this?

---

### Post by Ben2r25 on 2010-08-05
Bump

---

### Post by Ben2r25 on 2010-08-05
I uninstalled the alsa backports and installed the generic linuxant driver from [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) with only the line ```
options snd-hda-intel position_fix=0 enable=yes

```
active in the alsa-base.conf. Both headphones and the mic work properly now. The only issue with this is that, because the driver was compiled on this computer, it will no longer work when ubuntu updates the kernel in the future. The driver will need to be uninstalled and then reinstalled with every kernel update. Since this computer belongs to a friend who isn't tech savvy, I want to avoid this if possible. 

Is there a way to have this driver recompile automatically when a new kernel is installed? Or, maybe, there's a way to stop ubuntu from performing future kernel updates? (I would like to avoid this option if possible so that the computer can remain up to date)

---

### Post by utilitytrack on 2010-08-06
If you find solution for your general trouble please mark this thread as solved

---

### Post by commuted on 2013-03-25
I think the issue is that mono microphone is connected to the wrong side. I connected a mono USB microphone and wrote a program to capture audio. When I set it to stereo I had sound on one channel, when I set it to mono I had no sound at all. The issue that might explain everything is the front panel jack is wired wrong and software reversed it someplace breaking the other interfaces. All others, e.g. built in microphone or USB fail as mono devices. SInce they work as stereo devices it seems flaky. I don't know what to do about it.

---

### Post by overdrank on 2013-03-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

