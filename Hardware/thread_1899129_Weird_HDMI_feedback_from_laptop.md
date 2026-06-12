---
title: "Weird HDMI feedback from laptop"
date: 2011-12-22
forum: Hardware
---

### Post by jgray152 on 2011-12-22
I was never able to use the HDMI audio from my laptop with windows 7, Never could get it working right.

Ubuntu has it working every time but every 12 seconds there is this weird sweeping feedback which lasts for a split second on top of the audio already playing.

Don't know if I can take a recording of it but anyone have a clue?

Thanks

---

### Post by Shompol on 2011-12-22
Ctrl-Alt-T

**alsamixer**

if you don't have it installed try 
[B][FONT=Arial]
sudo apt-get install gnome-alsamixer[/FONT][/B]

Play around with channels. Maybe there is a channel that generates the feedback and you can simply turn it off.

---

