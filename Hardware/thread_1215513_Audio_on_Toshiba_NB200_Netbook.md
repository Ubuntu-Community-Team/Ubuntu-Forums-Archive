---
title: "Audio on Toshiba NB200 Netbook"
date: 2009-07-17
forum: Hardware
---

### Post by jesseAnger on 2009-07-17
I have just installed Ubuntu 9.04 on my Toshiba NB200 and after I fixed the Wireless thinking im home free i find that my audio is not working. Can i ask if anyone can help with how to troubleshoot and a potential fix for the issue. it sees lots of options for audio, its not telling me theres none. I dont have sound when something plays

Thanks in advance and let me know if you require anything to help me.

-Jesse

update on details found

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff6e
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by prshah on 2009-07-17
> **jesseAnger said:**
> i find that my audio is not working.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High 


It may be a problem with the speaker configuration. Right click your volume icon, and choose "Open Volume Control". Choose "Preferences" and check everything shown.

Max out all volumes, and unmute everything.

Open the "Switches" tab, and, if you have a setting "External Amplifier", please check it.

Now check the sound.

If it works, try muting the various audio sliders one by one to find out which one is being used. For example, you may find that to get speaker output, you may have to use the "Headphone" volume slider.

Post back with your results for further recommendations. If it doesn't work, a couple of screenshots of your Volume Control app showing all the sliders may be helpful.

---

### Post by Ultim8Fury on 2009-07-17
It's not levels, see my NB200 setup guide. 

[http://ubuntuforums.org/showthread.php?p=7631269#post7631269](http://ubuntuforums.org/showthread.php?p=7631269#post7631269)

or the thread that spawned it. 

[http://ubuntuforums.org/showthread.php?t=1204072&highlight=ALC272](http://ubuntuforums.org/showthread.php?t=1204072&highlight=ALC272)

---

### Post by jesseAnger on 2009-07-18
> **Ultim8Fury said:**
> It's not levels, see my NB200 setup guide. 

[http://ubuntuforums.org/showthread.php?p=7631269#post7631269](http://ubuntuforums.org/showthread.php?p=7631269#post7631269)

or the thread that spawned it. 

[http://ubuntuforums.org/showthread.php?t=1204072&highlight=ALC272](http://ubuntuforums.org/showthread.php?t=1204072&highlight=ALC272)



Your tips helped me solve more then one issue. Thanks for the help I'm loving my NB200 now.

---

### Post by tamerucar on 2009-07-19
Hi, 

I had a similar no-sound problem on my Toshiba laptop and I managed to fix it. Check it out here:

[http://ubuntuforums.org/showthread.php?t=1208041]("http://ubuntuforums.org/showthread.php?t=1208041")

Please notify me if it works for you or not.

---

### Post by i_surf_the_turf on 2010-03-10
I'm afraid it doesn't work on the TOSHIBA NB200.

---

