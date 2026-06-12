---
title: "Adding a missing screen resolution to settings"
date: 2009-03-22
forum: Hardware
---

### Post by sa125 on 2009-03-22
I have a 19" philips screen on my desktop, which works great at 1280x1024 resolution. I've just added an identical screen, but now this resolution doesn't appear in the Monitor Resolution Settings dialog. How can I make it re-appear?

---

### Post by dwasifar on 2009-03-22
Are you using the Nvidia proprietary drivers?  If so, set your dual monitor setup using nvidia-settings rather than the regular resolution settings utility.  (You may need to start it manually from terminal.)

---

### Post by sa125 on 2009-03-22
> **dwasifar said:**
> Are you using the Nvidia proprietary drivers?  If so, set your dual monitor setup using nvidia-settings rather than the regular resolution settings utility.  (You may need to start it manually from terminal.)

I'm not sure. The single screen worked fine before, I just added an identical one and the resolution vanished. How do I use the nvidia-settings? Do I need to install a package or something?

---

### Post by sa125 on 2009-03-22
> **sa125 said:**
> I'm not sure. The single screen worked fine before, I just added an identical one and the resolution vanished. How do I use the nvidia-settings? Do I need to install a package or something?

I installed the nvidia-settings package and tried to config with it, but all it did was mirror the screen on both displays. Any clue how to solve this problem? It all worked find before, but the extra screen messed something up. thanks!

---

### Post by norwoods on 2009-03-22
start the nvidia gui interface with gksu nvidia-settings in a terminal window.  when the nvidia gui interface is running, click X Server Display Configuration. 
click Configure...
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit

---

### Post by sa125 on 2009-03-23
My graphics card is Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02), so that's probably why the nvidia-settings tool don't do much.. How can I handle the dual displays for an intel card?

---

### Post by sa125 on 2009-03-23
please see thread:
[http://ubuntuforums.org/showthread.php?p=6941746#post6941746](http://ubuntuforums.org/showthread.php?p=6941746#post6941746)

---

