---
title: "Dual display options"
date: 2008-07-11
forum: General Help
---

### Post by Roger D on 2008-07-11
Hi

I've been experimenting with dual displays, with limited success.

I'm running 8.04, I've got Nvidia X Server Settings installed, and I've got an Asus EN6200LE, graphic card, with DV1 and VGA outputs. I normally use a 19in digital monitor with a resolution  of 1440x900. In my work I spend a lot of time comparing two documents - I generally try to put them side by side, but it gets a bit cramped. I've got a second, old, 17 in analogue monitor, with a resolution of 1280x1024.

I connected my two second monitors, with the old monitor plugged into the VGA output, and via selecting the twinhead option in Nvidia X Server I was able to get both displays working. Unfortunately, I couldn't see the bottom panel on my 1440x900 monitor, so it was a bit impractical.

I'm planning to ditch my 19 in 1440x900 monitor, and replace it with a second 17in 1280x1024 digital monitor, and then run the two 17 monitors together.

Is this a good idea?

Does anyone have any other suggestions?

Roger D

---

### Post by fedex1993 on 2008-07-11
coundl't you just change the resolution on the 19 inch monitor to 1280x1024 so the 17 inch monitor will look the same even thoe it will not be as clear thoe

---

### Post by Roger D on 2008-07-12
It's an idea, but I don't think I can have a resolution higher than the number of pixels on my display, so 900 into 1024 won't go.

Roger D

---

### Post by DukeNuke2 on 2008-07-12
> **Roger D said:**
> It's an idea, but I don't think I can have a resolution higher than the number of pixels on my display, so 900 into 1024 won't go.

Roger D

who is vendor of your monitor/s? please give also the modell type of your monitor/s

---

### Post by Roger D on 2008-07-12
Thanks for the responses, but thanks to a very helpful blog on this problem [http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup](http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup)

I've now solved the problem. There are two key things to bear in mind when using NVIDIA X Server Settings:

1 You're going to be changing the X11 config file, so you need to be in super user mode, so do it via the terminal using sudo nvidia-settings

2 If you have screens with different resolutions, like me, then you have to re-start before you see bottom panel bars - just opting to appying the new settings doesn't work. Otherwise nvidia setting just fine.

I'll probably buy a new monitor, so that I've two monitors with the same resolution, but really I'm very pleased with how it's currently working .

Roger D

---

