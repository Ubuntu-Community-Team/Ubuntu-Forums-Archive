---
title: "please assist w/ nvidia drivers ppc"
date: 2009-09-25
forum: Hardware
---

### Post by gwydionwaters on 2009-09-25
i have found a lot of info on compiling special kernels etc and am not sure what to go by. i have a geforce fx go5200 and am running 8.10
is there anyone who has used nvidia drivers with a ppc before? or compiled the drivers from source? any help with either route would be awesome

---

### Post by dagoth_pie on 2009-09-25
I'm currently running a Geforce 5200 with the 173 drivers from the repositories if you go to: System/Administration/Hardware Drivers

Is there anything showing up there?

---

### Post by gwydionwaters on 2009-09-25
just my broadcom drivers

---

### Post by dagoth_pie on 2009-09-25
try running
```
sudo apt-get install nvidia-common
```
in the terminal, then see what shows up under Hardware drivers.

---

### Post by gwydionwaters on 2009-09-25
almost, i got ```
Package nvidia-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-common has no installation candidate
```
maybe i need to add a repository? know what it might be?

---

### Post by dagoth_pie on 2009-09-25
You could try going into software sources and enabling things that look relevant, I can tell you it's showing up in mine, but I was mucking round not too long ago and have a lot of extra things enabled, no extra repositories though, just backports, proposed updates, etc. Maybe someone can tell you specifically what needs changing if you wait around...

---

### Post by gwydionwaters on 2009-09-25
hmm, thanks for the ideas. i did have backports and another one un-checked, i checked them off and tried again but still no luck. is your computer ppc or intel?

---

### Post by dagoth_pie on 2009-09-25
It's an x86, but I'd had assumed that the graphics card driver would work regardless of the cpu architecture.

Sorry about that, I need to learn not to assume so much, a quick google search came up with this FAQ

[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

So unfortunately all you can do is manage with the open source drivers which I don't think support 3d, or maybe send off an email to NVidia or wherever you bought your PC from, one email won't make a difference but if enough people do it...

---

