---
title: "Hardware volume control on FujitsuSiemens p7010"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by bengtfalke on 2005-10-13
I have a couple of buttons (keys) on my laptop for controlling the speaker volume. If I try to use them a small box shows up where the slider moves right and left without any change to the volume. If I instead move the slider in the speaker icon on the top row of the screen all works OK.

If I open the volume control program with a lots of sliders in it, I can see that the buttons affect the overall volume slider. But it is the slider named Headphone that controls the volume in reality. Is there a way to map these hardware keys to control the correct slider?

regards/falke

---

### Post by alge on 2005-12-06
You need to set the ac97_quirk option for the snd-intel8x0 module.

Create file /etc/modprobe.d/alsa-quirk with

[FONT="Courier New"]    options snd-intel8x0 ac97_quirk=1 [/FONT]

I found it there:

[http://linuxwiki.org/LinuxHardware/NoteBooks/FujitsuP7010En](http://linuxwiki.org/LinuxHardware/NoteBooks/FujitsuP7010En)

---

