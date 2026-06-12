---
title: "no sound for Terratec soundcard"
date: 2010-04-28
forum: Hardware
---

### Post by zsero on 2010-04-28
I have just tried the LiveCD of 10.04 and 9.10 and I have the same issue in both distributions: I have no sound out of my soundcard. 

My soundcard is a Terratec DMX 6Fire, based on Envy24 chipset. Ubuntu detects it fine, but where I can select between the outputs/inputs only digital in/out combinations are listed. I would like to listen to music on the standard stereo outs, not with on digital outs.

The soundcard works perfectly using the newest Puppy linux livecd with ALSA config. What can I do? Is there ALSA config in Ubuntu?

---

### Post by khelben1979 on 2010-04-28
This guy have working speakers with that soundcard, see [this thread]("http://ubuntuforums.org/showthread.php?t=607628"). Hopefully it can help you out some.

---

### Post by cascade9 on 2010-04-28
Doesnt 9.10/10.04 use pulseaudio by default? Could be that is the problem. That sound card sure looks like it works fine with alsa- 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Terratec](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Terratec)

Directions for getting it going here- 

[http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712)

---

### Post by zsero on 2010-04-28
Sorry guys, I don't understand. What is different in these new Ubuntus which make it hard to simply use ALSA config and have a working stereo sound? What is this Pulseaudio thing?

On the ALSA page, I have found a link to a Envy24 mixer project. It's called [http://sourceforge.net/projects/kenvy24/](http://sourceforge.net/projects/kenvy24/) Is it possible that using this program with the newest Ubuntu's would make it work?

What should I do with the .asoundrc file you linked from the other thread? Put it in etc/something and restart? Is it not possible to get a working config out of Puppy once it's running? (or maybe from older Ubuntu-s but I don't know which version worked last).

---

### Post by khelben1979 on 2010-04-29
> **zsero said:**
> What should I do with the .asoundrc file you linked from the other thread? Put it in etc/something and restart? Is it not possible to get a working config out of Puppy once it's running? (or maybe from older Ubuntu-s but I don't know which version worked last).

You could try and send the guy a pm and ask how he did it. I don't know myself other than that he wrote that he got it working and from the configuration file you see how it looks like when it does.

---

### Post by tobsco on 2010-04-30
I had the same problem with my m-audio audiophile 2496 and fixed it by following the instructions in post #52 from [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442").

Hopefully it will work for you as it uses the same envy24 chip and ice1712 drivers.

---

