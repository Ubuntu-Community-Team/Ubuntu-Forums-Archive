---
title: "MSI Z97 Motherboard Line Out Not Recognized"
date: 2016-12-17
forum: Hardware
---

### Post by xeronate on 2016-12-17
I recently installed Ubuntu 16.04 onto a partition of my hard drive and have run into a few hardware issues. Currently, I am trying to get the line out jack on my motherboard to work. I have already made sure that it is unmuted and the jack is properly identified as line out, but it won't show up as a device I can set as my default. When I was examining if the port was detected as line out it said it was disconnected.

The port works fine on my windows partition. Any advice?

This is a link to the motherboard. There aren't any linux drivers. [https://us.msi.com/Motherboard/support/Z97-PC-Mate.html#down-bios](https://us.msi.com/Motherboard/support/Z97-PC-Mate.html#down-bios)

---

### Post by oldfred on 2016-12-18
My old Windows XP system required me to unplug line out and replug it in, every time I updated driver in XP. It just worked in Ubuntu.

It seemed that ports were "smart" and needed to sense connection, but if already plugged in, would not reset internally.

---

### Post by xeronate on 2016-12-19
I appreciate the thought, but I have tried that many times. Anyone else? Any more info I can provide?

---

### Post by #&amp;thj^% on 2016-12-19
Can you give us the output of this from the terminal
```
inxi -C -A
```
Some where to start at least.

---

### Post by Yellow Pasque on 2016-12-20
> **xeronate said:**
> Any more info I can provide?

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

