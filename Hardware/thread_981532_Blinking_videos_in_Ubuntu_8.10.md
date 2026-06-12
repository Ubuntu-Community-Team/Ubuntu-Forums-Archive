---
title: "Blinking videos in Ubuntu 8.10"
date: 2008-11-13
forum: Hardware
---

### Post by Szabolcs SU on 2008-11-13
I am new to Ubunto(8.10). I have a laptop with Ati mobility radeon x1600. When I try to play videos, they are blinking. I tried to install the factory driver for it. Every went fine, but I still only see the driver that was originally installed by ubuntu(in system menu) and the videos are still blinking.

Help needed!

---

### Post by binbash on 2008-11-13
open your video player's preferences ( i use vlc) search for video output there and make it X11.This will fix it.

---

### Post by frankleeee on 2008-11-13
> **Szabolcs SU said:**
> I am new to Ubunto(8.10). I have a laptop with Ati mobility radeon x1600. When I try to play videos, they are blinking. I tried to install the factory driver for it. Every went fine, but I still only see the driver that was originally installed by ubuntu(in system menu) and the videos are still blinking.

Help needed!

what type of videos, and what have you installed as far as media addons or codecs.

---

### Post by Mardoct909 on 2008-11-13
Try using envy to install drivers for you.

```
sudo apt-get install envyng-gtk
```

will get it for you, then you can find it under Applications-> Utilities (I think. Look around if it isn't there.)

This program auto-detects and installs/configures the correct drivers as necessary.

---

### Post by Szabolcs SU on 2008-11-13
It works! Thanks a LOT! Blazing fast reply. You've made me much more devoted to Ubuntu! (changed video output to X11)

---

### Post by binbash on 2008-11-13
> **Szabolcs SU said:**
> It works! Thanks a LOT! Blazing fast reply. You've made me much more devoted to Ubuntu! (changed video output to X11)

You are welcome ;)

---

### Post by Szabolcs SU on 2008-11-13
Is there a way to make all the players work correctly? With most of them I don't find a way to set their video output to X11. For example if I want to watch a video while still streaming it.

---

