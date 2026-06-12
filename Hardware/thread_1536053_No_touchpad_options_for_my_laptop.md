---
title: "No touchpad options for my laptop"
date: 2010-07-21
forum: Hardware
---

### Post by haran_hockey on 2010-07-21
So the touch pad works, as in I can move the mouse around, left and right click work, but there's no touchpad options in System>Preferences>Mouse

I use an old Toshibal Satellite which uses a Synaptics touchpad.

Basically, I want 2-finger scrolling, but before I do that, I think I should at least figure out a way to get the touchpad options.

Also, when I typed in **synclient -m 100** in terminal, I got this:
```

Can't access shared memory area. SHMConfig disabled?
Couldn't find synaptics properties. No synaptics driver loaded?
```

---

### Post by thelethargarian on 2010-07-21
What distro and version are you running, e.g. Ubuntu 10.04? For the 2-finger scrolling, you should be able to do
```

synclient -l

```
Then you can just do 
```

synclient EmulateTwoFingerMinZ=0
synclient EmulateTwoFingerMinW=6
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient VertScrollDelta=75
synclient HorizScrollDelta=100

```

Those parameters may not be exactly right for what you want, so you can change them.

I don't know why the options wouldn't appear.

---

### Post by haran_hockey on 2010-07-21
First off, I'm using Ubuntu 10.04

When I type in synclient -l, I get: Couldn't find synaptics properties. No synaptics driver loaded?

This is my main problem.

---

### Post by haran_hockey on 2010-07-22
So... how can I enable these options?

---

### Post by Ian Sinclair on 2010-11-19
I found that my Acer Aspire running Ubuntu 10.04 had no touchpad options, but after I enabled WiFi the touchpad options tab appeared. Weird, but useful.;)

---

