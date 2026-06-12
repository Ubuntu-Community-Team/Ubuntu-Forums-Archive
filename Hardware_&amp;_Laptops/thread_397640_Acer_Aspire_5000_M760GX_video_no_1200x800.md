---
title: "Acer Aspire 5000 M760GX video no 1200x800"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by FNGtyler on 2007-03-30
I have a Acer aspire 5000 with a SIS M760GX video card i can set the display in windows to 1200x800 but its not listed in screen resolution in ubuntu. Is it possible to get that setting in ubuntu? Is my video card no actually set up properly?

---

### Post by teaker1s on 2007-04-02
Firstly please use this command in terminal and post the output
```
 lspci | grep VGA
```

---

### Post by jodufi on 2007-04-02
You have to install 915resolution (using Synaptic) to enable the resolution 1280x800.
I don't remember if there is any other step, like modify xorg.con and put 1280x800 in Modes.

---

