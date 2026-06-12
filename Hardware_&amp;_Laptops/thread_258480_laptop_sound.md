---
title: "laptop sound"
date: 2006-09-16
forum: Hardware &amp; Laptops
---

### Post by cottonwood on 2006-09-16
alright. i'm dual booting ubuntu and kubuntu on my compaq presario v3020us notbook.
when i plugin speakers or my headphones, the laptop speakers still produce sound (both ubuntu and kubuntu)? how can i fix this?  

also, how come the sound up, down and mute buttons work in ubuntu but not kubuntu? i thought the only diff between the 2 were gnome and kde...

---

### Post by cms1082 on 2006-09-16
open up your volume controls and select switchs there should be a box to check that will mute the laptop speakers when you plug in headphones i had the same problem so i looked around till i found it hope it helps

---

### Post by JPMaximilian on 2006-09-16
The only way I could fix this problem was to installed the latest alsa drivers, if the previous poster's fix didn't work and you're interested, I'll explain how to do it.

---

### Post by cottonwood on 2006-09-16
> **cms1082 said:**
> open up your volume controls and select switchs there should be a box to check that will mute the laptop speakers when you plug in headphones i had the same problem so i looked around till i found it hope it helps
i'm not seeing the switches.  when i open volume control, all i see is master vol, pcm and capture....
however, i did notice that i there seems to be two different sound devices
a generic 14f1 id 5047 (oss mixer) and hda intel (alsa mixer). does this have anything to do w/it?

---

