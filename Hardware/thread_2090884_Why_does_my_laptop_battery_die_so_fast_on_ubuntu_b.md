---
title: "Why does my laptop battery die so fast on ubuntu but not on windows?"
date: 2012-12-03
forum: Hardware
---

### Post by silysnipe on 2012-12-03
when im on windows my battery will last me at least 8 hours, on ubuntu though, it lasts 2. why?

---

### Post by boogerama on 2012-12-03
I have a similar issue on my older Dell XPS1340.  On Windows I used to get about 5+ hours on my extended battery.  Now I get about 3ish

It could be a slew of things but I would start with making sure you have the correct drivers for everything.

Start by making sure you have the correct video drivers installed if you have discreet graphics.  In my case my fan runs more on 12.04 than it does on Windows.  

As much as it sucks to hear this, battery life is a big point of contention with a lot of people and Linux

Sorry I couldn't be of more help.

---

### Post by dniMretsaM on 2012-12-03
Battery life isn't Linux's strong point. One of the best things to do, however, is install Laptop Mode Tools:
```
sudo apt-get install laptop-mode-tools
```

---

### Post by offgridguy on 2012-12-03
What actually does Laptop Mode Tools do?  Just curious, before i install it.
Thank's. :)

---

### Post by dniMretsaM on 2012-12-04
Reading the comments in the configuration file is probably the best way  to get to know LMT. You can read it without installing anything  [here](https://github.com/rickysarraf/laptop-mode-tools/blob/master/etc/laptop-mode/laptop-mode.conf).

---

