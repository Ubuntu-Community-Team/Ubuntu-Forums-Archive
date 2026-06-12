---
title: "Intel i7 and Ubuntu 10.04"
date: 2010-05-23
forum: Hardware
---

### Post by jmwolf27 on 2010-05-23
Hi,

I have an i7 860 Lynnfield system with 2 HDDs, one for Windows 7 and the other for Ubuntu 10.04. I have the 64-bit version of both Win 7 and Ubuntu 10.04. I am having concerns about Ubuntu though in comparison to Windows 7. The thing is that in Ubuntu in the system monitor window, Ubuntu occasionally will max out one of the 8 processor cores (4 are virtual) while Windows 7 won't even show that my processor is required to work past 20% of its capacity. I am concerned about this. Is there a patch that I could apply or is there an update coming for this? I really shouldn't be maxing out a processor core at all.

---

### Post by dino99 on 2010-05-23
on my multi-cores system, if any services or apps are used, the cores are quiet.
So you have something running in the background

---

### Post by inso_741 on 2010-05-23
Try killing update notifier and see if it helps...;)

---

### Post by jmwolf27 on 2010-05-23
I have noticed this when it initially loads and when I was installing some software. Shouldn't the load be evenly distributed amongst the cores?

---

### Post by inso_741 on 2010-05-23
> **jmwolf27 said:**
> I have noticed this when it initially loads and when I was installing some software. Shouldn't the load be evenly distributed amongst the cores?

No it shouldn't cause almost all the apps are single threaded...that means one application can use only one core at a time......more cores allow you to multitask that is run multiple apps simultaneously...

---

### Post by 3Miro on 2010-05-23
Does windows show you the usage of each individual core? It used to be that you need to install extra software for that. 20% in windows would mean that one core is maxed or close to maxed.

If you see one core maxed it means something crashed in the background. If you are running an app and it usurps one full core, this is standard optimal behavior.

---

### Post by renkinjutsu on 2010-05-23
I remember there was some powersaving kernel feature. I don't remember what it's called, but when idle, it basically keeps all operations on one core so that the other cores may remain in a idle state to save power

---

### Post by jmwolf27 on 2010-05-23
Interesting, I haven't seen where I could do the break down in Windows to see each core. I have not really seen it over 20% and it doesn't really reach there that much only when I have a lot going on. I am just wanting to make sure that I do not burn out a core and that if this is normal or not. I really appreciate everyones contributions.

---

### Post by inso_741 on 2010-05-23
don't worry...you can't burn out an intel core that easily
I've an i7 920...I've disabled HT and still have no problems multitasking

---

### Post by Ophidion on 2011-01-25
try typing 'top' in a terminal.

---

