---
title: "X.org problem, TV out doesn't work"
date: 2008-09-03
forum: General Help
---

### Post by roccivic on 2008-09-03
Hi,
I have installed Xubuntu on a relatively old PC (866MHz, 192MB RAM, 4MB ATI 3D rage with TV out). And I would like to use a TV instead of a monitor.

The thing is that it doesn't really work. The TV out of the video card only works when the PC is just turning on, it shows the BIOS stuff, the boatloader and even a grapical splash screen with a picture of a mouse. As soon as X.org starts the screen goes white. When using a regular monitor everything works perfect.

Any ideas on how to solve this problem?

Many thanks, Rouslan.

---

### Post by roccivic on 2008-09-03
Just tried Puppy linux, where if I selected X.org it didn't work, but with Xvesa it worked fine.

Also the TV has a 16:9 aspect ratio and is connected to the PC via a coaxial cable, which (i think) carries a composite video signal.

Rouslan

---

### Post by roccivic on 2008-09-04
bump

---

### Post by roccivic on 2008-09-06
Problem solved. The solution was to install the open-source ATI driver, instructions were found in the community maintained documentation.

Peace

---

