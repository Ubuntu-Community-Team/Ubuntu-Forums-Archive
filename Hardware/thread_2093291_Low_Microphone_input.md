---
title: "Low Microphone input"
date: 2012-12-10
forum: Hardware
---

### Post by SirLouen on 2012-12-10
I've recently installed Ubuntu 12.10, and I've found that although the microphone is working, I have to put it really near my mouth in order to get proper sound. And there is like a noise in the background constantly.

I have Windows in the other partition, and It works perfectly, no noise, and I can put the microphone like 4 or 5 cm away from mouth and it receives sound perfectly, so there is a problem with my Ubuntu settings.

What shall I do?

---

### Post by irv on 2012-12-10
What is your mic setting?
[ATTACH]228495[/ATTACH]

---

### Post by dannyboy79 on 2012-12-10
open a terminal and type in the following command
```
alsamixer
```
then i think you use tab to switch to inputs and use the left and right arrows to go to your input device whether it's line in or microphone and then use up arrow to turn up the volume. also make sure it has 00 instead of MM, if it's MM that means it's muted, use the M button to unmute it.

---

### Post by irv on 2012-12-10
I am not sure what version of Ubuntu you are using, but in most versions you can simply click on the sound icon in the top panel and select sound setting and go to the tab "Input".

---

### Post by dannyboy79 on 2012-12-10
> **irv said:**
> I am not sure what version of Ubuntu you are using, but in most versions you can simply click on the sound icon in the top panel and select sound setting and go to the tab "Input".that is true but sometimes alsamixer values are either muted or low so I suggested that first, next would have been the sound icon.

---

