---
title: "Screen resolution changes at startup"
date: 2009-04-04
forum: Hardware
---

### Post by dehyde on 2009-04-04
Greetings.

My Ubuntu seems to have a strange problem I don't quite understand.
I'm working at a screen resolution of 1280X1024 on 75hz, and almost each time I restart my computer, it changes to something else (can't figure out what resolution is it).

When I open my screen resolution settings it automaticly brings up 1280x1024 60hz as the first option. 

So practicly each time I restart my system I need to manually reset the screen res.

Any ideas?

---

### Post by overdrank on 2009-04-04
Hi and welcome, what is the model of the graphics card? You may use the command lspci in the terminal which is located under applications, accessories. Look for VGA, you may also look under system, Administration hardware to see if any drivers are available.

---

### Post by dehyde on 2009-04-04
ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by overdrank on 2009-04-05
> **dehyde said:**
> ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Hi and sorry for the delay. If you are using Intrepid 8.10 then you may look at [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

