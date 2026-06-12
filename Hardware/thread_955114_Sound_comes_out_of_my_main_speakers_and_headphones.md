---
title: "Sound comes out of my main speakers and headphones at same time"
date: 2008-10-21
forum: Hardware
---

### Post by Black Blade on 2008-10-21
I'm running Hardy Heron on my Toshiba Satellite A135-S4527 and my sound card is:
Card: HDA Intel 
Chip: Realtek ALC861-VD
Can someone tell me how to fix this I've tried many things I already found on the Ubuntu forum.

---

### Post by Dark_Stang on 2008-10-21
Open up the file /etc/modprobe.d/alsa-base and add "options snd-hda-intel model=laptop" to a new line, then save it and reboot.

---

### Post by Black Blade on 2008-10-21
That didn't work do you have any other suggestions?

---

### Post by Black Blade on 2008-10-21
Can anyone help?

---

### Post by Toshibawarrior on 2008-11-20
Hello...for more info about Toshiba Satellites and Linux visit my blog (it's still under construction and I haven't been able to post in a while...sorry about that...but I"ll keep it as up-to-date as possible. Link is on my signature.).

Simply open up a terminal and type[

CODE]gksudo gedit /etc/modprobe.d/alsa-base[/CODE]

And on the very end of the file (remove any other option you've added to the end) add this line:

```
options snd-hda-intel model=lenovo
```

Yep, Lenovo...don't know why but it's the only option that works for my laptop and it's the only one that makes my speakers go quiet when the headphones are plugged in...The only downside it's that you must plug the headphones when the volume is **not** muted. If you plug headphones with muted sound the speakers will sound too.

Try it and let me know if you need any more help.

---

