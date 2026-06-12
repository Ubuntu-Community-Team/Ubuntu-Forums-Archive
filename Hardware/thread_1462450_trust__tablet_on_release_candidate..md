---
title: "trust  tablet on release candidate."
date: 2010-04-25
forum: Hardware
---

### Post by oggeking on 2010-04-25
So I've been trying to get my trust slimline design tablet tb-5300 to work on the 10.04 release candidate but nothing seems to be working. I've followed all the guides about wizardpen that I was able to find but no luck there. So my question is does anyone know how to get it to work if its even possible. 

I hope you understand what I'm trying to say. Also I would like to apologize for any spelling mistakes, I'm from Sweden so english is just a second language for me.

[B][I][B][SIZE=1]
[/SIZE][/B][/I][/B]

---

### Post by Favux on 2010-04-25
Hi oggeking,

Welcome to Ubuntu Forums!

First let's make sure it's a WizardPen tablet.  Enter in a terminal:
```
grep -i name /proc/bus/input/devices
```

Is the WizardPen driver in Synaptic Package Manager?  My guess is the WizardPen drivers you've been looking at won't compile on the 1.7 Xserver Lucid has.

Hope this is helpful.

---

### Post by oggeking on 2010-04-26
Thanks for the response i ran the command and the system finds a tablet. I guess its just like you said it won't compile.

Thank anyways.

---

