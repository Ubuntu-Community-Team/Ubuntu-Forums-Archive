---
title: "Ubuntu OpenGL performance problems with NVIDIA"
date: 2017-10-13
forum: Hardware
---

### Post by tonyphillips7777 on 2017-10-13
I am running Ubuntu 16.04.3 LTS with kernel 4.4.0.

My workstation:

Hewlett Packard Z840
Dual 12C Xeon E7 v3 CPU
48GB RAM
NVIDIA Quadro K4200

Now on to the video card problem. 

If I use the proprietary NVIDIA drivers with Heaven OpenGL Benchmark tool I get:

[LIST]
[*]~17 FPS
[*]GPU utilization pegged at 100% always
[/LIST]

If I use nouveau drivers with Heaven OpenGL Benchmark tool I get:
[LIST]
[*]2 FPS <--YES only 2 FPS!!!
[*]GPU utilization pegged at 100% always
[/LIST]

I have tried other NVIDIA video cards (K2200) and got the same result. I have tried the latest propitiatory drivers and older ones with the same result.

Does anyone know what the issue is?

When running propitiatory drivers I disable and blacklist nouveau of course.

The funny thing is when I run a older (much older) AMD 7950 card my nouveau performance is much better: (20 FPS)

I have also tried other OpenGL benchmark tools and got the same results.

This is a very clean (new install) environment too.

Thanks for any help.

---

### Post by Autodave on 2017-10-13
According to Nvidia's website, you should be using the 384.90 driver.

Now, where did you get the driver from? The safest way is to either go into the software center or use synaptic package manager to install.  Alternatively, go to Settings -> Additional drivers  and let it look for you and then install it.

---

### Post by tonyphillips7777 on 2017-10-13
Yes I have 384.90 installed. It does this for 384.90 drivers and the earlier ones too. Any thoughts on what could be happening??

Thanks

---

### Post by Autodave on 2017-10-13
Where did you get the driver from?

---

### Post by tonyphillips7777 on 2017-10-13
NVIDIA via Ubuntu software and updates.

---

