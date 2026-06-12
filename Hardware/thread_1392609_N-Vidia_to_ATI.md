---
title: "N-Vidia to ATI"
date: 2010-01-28
forum: Hardware
---

### Post by crabhunter on 2010-01-28
I have just had to replace the graphics card in my old work pc and the only one I had lying around was an ATI. It did have an Nvidia.
I was hoping it would detect the new card and configure it, but it now boots into low graphics and expects me to do the work.
I'm using 9.10, how do I delete the old nvidia drivers and install Ati?
I tried going into hardware to dissable nvidia but in this low mode it doesn't show the nvidia drivers so I can dissable them.
Mike

---

### Post by MaindotC on 2010-01-28
It depends on the type of ATI card you have because a lot of older cards (like my x850) are not compatible with 9.04 and above.  Just get into a terminal and install the xorg-driver-fglrx package.

---

### Post by crabhunter on 2010-01-28
seems mine is not compatible, I think I will turn out my junk and see if I can find another nvidia.

---

### Post by MaindotC on 2010-01-28
If it's not compatible then you need to run 8.10 and below in order for the ATI driver to work.

---

