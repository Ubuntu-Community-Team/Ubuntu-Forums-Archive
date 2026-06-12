---
title: "Nvidia GeForce 9600 GT problems"
date: 2014-09-08
forum: Hardware
---

### Post by Guyofdoom42 on 2014-09-08
When I use it, the resolution goes to 640x480, and the screen is just really weird. Not sure how to explain it.

How do I solve this!?!?

---

### Post by gifford on 2014-09-09
You are probably running the open source driver for your card.
Let's start by getting some basic information:
What version of Ubuntu are you running?
In a terminal, run this command: lshw  -c video
Please provide the information it lists.

---

### Post by oldfred on 2014-09-09
I have a nVidia 9600GT and on first boot after install using nomodeset it is at low resolution. 

But first thing I do is install nVidia proprietary driver from repository. I usually use newest available, but they announced that 340.xx will become a legacy version and last available for this model card. I do not think Ubuntu has the new 340.xx or any later versions that were just released or beta in repository.

---

### Post by Guyofdoom42 on 2014-09-10
I already had the propietary driver, but I solved the problem by switching the DVI port, of all things.

---

