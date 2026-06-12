---
title: "Asus M2N-MX motherboard: onboard sound"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by hvymtlsteve on 2007-09-13
Hi guys... I have feisty running on an Asus M2N-MX motherboard, and having troubles with the onboard sound (Nvidia). 
When I was using Dapper I couldn't get any sound at all. After upgrading to feisty, I get some sound, but it is accompanied by a high-pitch squeal, and if I change the volume on the control panel, it just goes dead. 
Any ideas how to fix it?

Edit-- 
I do get this when I do an lspci:


00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

---

### Post by Storm Rider on 2007-09-24
I have the same problem :(

---

### Post by hvymtlsteve on 2007-09-24
There was a thread just yesterday or the day before that fixed this for me! 
Let me dig it up...

---

### Post by hvymtlsteve on 2007-09-24
[http://ubuntuforums.org/showthread.php?t=557892](http://ubuntuforums.org/showthread.php?t=557892)

Here it is!
Without looking at the thread, off the top of my head I think all I had to do was add to xorg.conf the following:

```
options snd-hda-intel index=0 model=3stack
```

But take a look at that thread just to be sure.

This is a common thing that needs to be done for some reason... just got a new laptop yesterday and a very similar line was part (but not all) of the sound fix.
EDIT-- ah yes, have to reinstall alsa-utils as well...

---

