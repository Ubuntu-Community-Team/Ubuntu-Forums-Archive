---
title: "Dell keyboard sound keys control microphone, not master"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by DFLiddle on 2008-03-04
My Dell Latitude D610 runs 7.10 beautifully. The hard drive was transferred from a D600 without a single hiccup, which impressed me.

The only issue, which I discovered today when attending a class and muting the sound, is that the special buttons on the hinge cover are controlling the microphone volume, *not* the master volume. The keyboard shortcuts -- Fn+End (Mute), Fn+PageUp (Volume up), and Fn+PageDn (Volume down) -- are also affected in the same way.

With what command or menu can I restore the correct settings?

---

### Post by Tuomas on 2008-03-24
Anyone? I have the same problem with my Fujitsu Siemens Amilo Pro.

---

### Post by Tuomas on 2008-03-25
This worked for me:

Write on a terminal:
gnome-sound-properties
At the bottom of the window highlight the channel you want to control via multimedia keys on your keyboard.

---

### Post by DFLiddle on 2008-03-26
Thanks for the tip! Once you pointed out the section of the Sound Preferences dialog, it was really a no-brainer. I just couldn't see that "Microphone" was selected further down in the list.

---

