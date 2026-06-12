---
title: "*Newbie* Touchpad not working"
date: 2011-09-02
forum: Hardware
---

### Post by Britahtah on 2011-09-02
Hello,

I'm new to Ubuntu. I just installed version 11.04 on my brand new laptop (Packard Bell EasyNote TS44-HR-060FR), and it looks great, but I can't seem to get my touchpad to work. 

I've tried everything on this page: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) but nothing changed.

I was wondering if anyone's experienced the same problem and knows how to solve it.

---

### Post by Britahtah on 2011-09-02
I'm sorry but I didn't get anyhthing of your message. "now if you say then nothing can be done" ?

And what does my question have to do with a headset?

---

### Post by ajgreeny on 2011-09-02
Try installing  **xserver-xorg-input-synaptics** and **gpointing-device-settings** and see if that helps.

Occasionally it appears that a touchpad might be detected as a mouse and the first of the above is not installed automatically.

Also can you show the output of ```
synclient -l
```in terminal.

---

