---
title: "Help a new user undervolt, kind of urgent"
date: 2009-11-01
forum: Hardware
---

### Post by DDDa on 2009-11-01
Hi, I'm sorry if there is something about this, but I've been searching all day...

Basically, I'm trying to move again (like, the 10000000th time, look at my join date) to Ubuntu, from Windows, for all the reasons you know. And I like Gnome better. :)

Straight to the point: I need to undervolt my 5 to 6 yrs old, ICH-4 Pentium M (Dothan 1.7) laptop. It's absolutely necessary because it generates a lot of heat. It's undervolt or Windows, unfortunately, as I prefer to deal with viruses than heat/noise.

So, is there any instructions on Karmic? How is PHC?

Thanks in advance,
David

---

### Post by peculiar penguin on 2009-11-01
There's a thread [here]("http://ubuntuforums.org/showthread.php?t=786402"), but I think the tutorial hasn't been updated for a while now.

Badly oversimplified summary: Add [this PPA]("https://launchpad.net/%7Elinux-phc/+archive/ppa") to your software sources, and Update Manager should install a PHC-patched kernel assuming one is available. Reboot, make sure the kernel module loads, check /sys/devices/system/cpu/cpu0/cpufreq/phc_controls. If you're undervolting under Windows, you should be able to convert your known voltage settings to the format PHC uses. Echo your settings into the file mentioned above and stress your system for a bit, if it doesn't crash you can add the echo line to rc.local to have your settings applied automatically on startup.

It looks like the PPA has a kernel for Karmic, but I haven't had time to try it yet. Everything worked fine in Jaunty though, you just need to pay attention when approving updates - don't install/run new kernels before the patched version is available, or you'll be running at full voltage in the meantime.

---

### Post by zcats on 2009-12-23
Yes. add ppa as above, but you still need to patch kernel

[http://ubuntuforums.org/showthread.php?t=1311873&highlight=undervolt:P](http://ubuntuforums.org/showthread.php?t=1311873&highlight=undervolt:P)

---

