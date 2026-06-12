---
title: "How do  you disable a single processor in a quad core?"
date: 2010-08-27
forum: Hardware
---

### Post by brucewestfall on 2010-08-27
I have a quad core processor that seems to have a problem with processor 2.  Every time it locks up and I have a terminal window showing error messages, processor 2 is at fault.

I get a total system lockup at least once a day and ANYTIME I do something processor intensive.  I know I can buy a new one, but would really like to disable 1/4 of my processor and see if that gets rid of the crashes.

Or any other ideas are welcome.

Thanks fellow Ubuntuians!  ( was that a race on Star Trek?!?!)

---

### Post by davidmohammed on 2010-08-27
Have a look at the bios options.  Often there is a way to disable one or more of the cores.

---

### Post by brucewestfall on 2010-08-28
Nope, my BIOS does not have that option.

Can Linux do it?  There is some command called cpufreq and other settings at /sys/devices/system/cpu/ that seem to control the processors.  Problem is, I cannot find any documentation about it.

Sure would like some starting point.  Just not sure where else to look.

Right now, I'm trying some things on this page - [http://xlife.zuavra.net/index.php/70/](http://xlife.zuavra.net/index.php/70/)

---

### Post by brucewestfall on 2010-08-28
OK, update time!  Not solved, but somewhat cured...

I installed the frequency scaling monitor (4x) and set each one for powersave, so that each cpu only runs at half speed.  Blender, which would crash within 30 seconds of a full on render has run without problems for 150 frames.

so I upped a processor to "On Demand".  Within just a few minutes, lockup again.

Don't know if it is just processor 2 or ANY of the cores running at full speed that crashes.

Still would like to shut down one core at a time.

Hopefully if anyone else has this problem, it is at least a fair fix until something better can be done.

---

