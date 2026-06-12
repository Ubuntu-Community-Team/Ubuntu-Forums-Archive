---
title: "Who doesn't love nvidia"
date: 2012-02-09
forum: Hardware
---

### Post by DoneRightI.T. on 2012-02-09
I think the nvidia support has always been the primary reason drawing me to purchase nvidia cards, as well to use Ubuntu as My O/S of choice.

however, with the above said, I have had nothing but heat issues with my new laptop with an i5 processor and a GeForce GT 330M

So I have attempted to get rid of the nvidia within the modprobe by blacklisting it, but for reasons beyond my knowledge, it still gets loaded into the kernel.

At present my nvidia card sits at a nice 80 degrees on average, and at times will drop down to around 70... but still enough heat to actually effect the cpu, thus effecting performance is in the tank and using it as a "lap" top gives you 2nd degree burns.

any advice on how to get that under control would be great.

---

### Post by DoneRightI.T. on 2012-02-09
I forgot to mention that this is the case with 64 bit flash running in firefox. Kind of a large point to ponder as we are all frustrated with Flash support in linux...

---

### Post by mikewhatever on 2012-02-09
You could try locking the driver to perform in the lowest power mode by adding the following to xorg.conf:

```

Section "Device"
 Identifier    "Default Device"
 Option  "RegistryDwords" PerfLevelSrc=0x2222;PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"
 Driver  "nvidia"
EndSection

```

Note, you may already have /etc/X11/xorg.conf and the "Device" section in it. If that's the case, just add the Option line to it. When done, logout/login.

PS: Was going to ask the mods to move this to the cafe because of the thread title. What's wrong with descriptive titles?

---

### Post by DoneRightI.T. on 2012-02-09
> **mikewhatever said:**
> You could try locking the driver to perform in the lowest power mode by adding the following to xorg.conf:

```

Section "Device"
 Identifier    "Default Device"
 Option  "RegistryDwords" PerfLevelSrc=0x2222;PowerMizerDefault=0x3; PowerMizerDefaultAC=0x3"
 Driver  "nvidia"
EndSection

```

Note, you may already have /etc/X11/xorg.conf and the "Device" section in it. If that's the case, just add the Option line to it. When done, logout/login.

PS: Was going to ask the mods to move this to the cafe because of the thread title. What's wrong with descriptive titles?

Going to tias(Try it and See) thank-you very much for the prompt feedback.

I did, to no avail. Wouldn't even boot up with those configs in there.

---

### Post by mikewhatever on 2012-02-09
This could mean that you don't have the driver installed. Have you installed the nvidia driver?

---

