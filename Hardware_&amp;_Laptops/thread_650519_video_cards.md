---
title: "video cards"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by TheMouse on 2007-12-26
I'm running Ubuntu 7.10 on an Acer Extensa 5620. I was wondering two things:

1. How do I determine exactly which video card is on this computer? It says, "Up to 252 MB Mobile Intel Graphics Accelerator x3100," but I'd like to know exactly which one it is. Is there some command line thingy I can do to figure it out? Or some place where it just shows me?

2. What suggestions would you have for updating my video card, when I eventually do so? Is there any brand which works particularly well for Ubuntu?

Thanks in advance.

---

### Post by jespdj on 2007-12-26
It is an Intel X3100 graphics card. What more do you want to know? You can try the command lspci to see the exact name, but I doubt you'll get more information than that.

Is that a laptop or a desktop computer? Graphics cards in laptops are almost never interchangeable. If it's a desktop PC, get an nVidia card, as that will work best with Linux.

---

### Post by levi_fowler on 2007-12-27
I have the same video, its tricky to get it running right in gutsy,look up x3100 in the forums and you'll get a ton of info. 

 
i have it in my acer laptop, you have to do somee funky things to get it to work right, edit the source.list and such

its a shared memory video, its normally running 128mb but can go higher if needed, games etc...

---

