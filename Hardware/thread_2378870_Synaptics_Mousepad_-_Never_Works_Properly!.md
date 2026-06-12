---
title: "Synaptics Mousepad - Never Works Properly!"
date: 2017-11-28
forum: Hardware
---

### Post by bigalxyz123 on 2017-11-28
Hello forum,

Running Ubuntu 17.10 and Windows 10 on a Samsung R530 laptop with a Synaptics touchpad.

Touchpad works fine with Windows, but the motion of the pointer is quite jerky in Ubuntu. Ubuntu runs well otherwise, but this is annoying enough to make me not want to use it.

Can anyone suggest what the problem might be please, and how to fix it?

Many thanks,
Alan.

---

### Post by irv on 2017-11-28
Have you tried the setting for the touchpad?
You didn't mention this in your post.[ATTACH=CONFIG]277686[/ATTACH]

---

### Post by bigalxyz123 on 2017-11-28
Thank you. You mean the "Touchpad Speed" slider? Yes, I've moved that around. It works as expected but it doesn't help with the problem - ie my pointer is either slow and jerky, or fast and jerky!

---

### Post by superstalker on 2017-11-30
Have you tried:

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by bigalxyz123 on 2017-12-01
Thank you. I hadn't, but I have now! It seems to have helped with the jerkiness (or is it my imagination?!). However I can now see another issue - the pointer motion is still very different to Windows. In Ubuntu the touchpad motion seems to be extremely sensitive when moving slowly, whereas in Windows this doesn't happen, which makes fine control of the pointer a lot easier. Is this something to do with "acceleration"? I'm a bit confused.

---

