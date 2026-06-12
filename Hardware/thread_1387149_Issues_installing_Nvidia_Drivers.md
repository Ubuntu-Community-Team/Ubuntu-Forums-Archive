---
title: "Issues installing Nvidia Drivers"
date: 2010-01-21
forum: Hardware
---

### Post by gear.h34d.2012 on 2010-01-21
Title.

Basically, I can't get my Nvidia 8600M drivers to install (As if it wasn't obvious :D)

I get Synaptic to download the drivers fine (Gets the progress bar to 50%) and when it switches to installing the drivers...it stops. It makes no further progress. Any tips, fixes, suggestions?

System specs.

Dell XPS M1530
Intel Core 2 Duo 2.4GHz
Nvidia 8600M
3GB DDR2 SDRAM
250GB HDD

---

### Post by calis1981 on 2010-01-21
id download it from the nvidia site
i've never had a problem doing it that way, but when its auto-mated i seem to always have problems, onces its installed all you have to do is make sure your device driver is "nvidia" and reset X

---

### Post by gear.h34d.2012 on 2010-01-21
I've tried that but the drivers I get from their site are .run files. I've searched around and have yet to find out how to run that file extension. Suggestions?

---

### Post by gear.h34d.2012 on 2010-01-21
Bump.

---

### Post by SamD42 on 2010-01-21
This thread explains it well:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Be aware you need to use the command 'sudo service gdm stop 'instead of 'sudo /etc/init.d/gdm stop' in 9.10.

---

### Post by gear.h34d.2012 on 2010-01-21
Much appreciate. I'll check it out.

---

### Post by gear.h34d.2012 on 2010-01-21
It worked. Much appreciated man.

---

