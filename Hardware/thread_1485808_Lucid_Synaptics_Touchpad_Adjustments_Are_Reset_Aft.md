---
title: "Lucid: Synaptics Touchpad Adjustments Are Reset After Suspend/Resume"
date: 2010-05-17
forum: Hardware
---

### Post by ifreecarve on 2010-05-17
I'm trying to permanently disable tap-to-click on my synaptics touchpad (dell latitude E6500).  

I can execute these commands, and they work.
```
#turn off synaptic (id #12) tap-to-click (id #293)
xinput set-int-prop 12 293 8 0 0 0 0 0 0 0

#another way
synclient MaxTapTime=0

```

The problem is that when I suspend/resume, the tap-to-click feature is active again.  VERY ANNOYING.  Is there a script that I gets run on every resume, or is there a configuration file that I should edit to make these changes permanent?

---

### Post by Kensey on 2010-05-17
Since one method you've used is to set MaxTapTime to 0, you might want to just do that in your xorg.conf (you may need to generate one; I forget how to do that but I bet a search on the forum will tell you how...).  Just give [the arguments to the synaptic driver]("http://linux.die.net/man/5/synaptics") in the appropriate section as listed in that link.

If you don't use or want touchpad-scroll, you can also set TouchPadOff=2 in xorg.conf.

---

