---
title: "switching from intel graphic card to amd"
date: 2017-05-23
forum: Hardware
---

### Post by heron1337 on 2017-05-23
yo is it possible to switch from integrated card to dedicated ? if it is can some1 explain how to do it?

---

### Post by Bucky Ball on 2017-05-23
You don't give much information about the AMD card you're looking at or your machine so this is it. Put the card in, switch the machine on, go to 'Additional Drivers' and see if there is a driver for the card or it 'just works' and the driver is in the kernel. You may need to go into BIOS and switch off the internal graphics (if you find an option to do that). 

With details of the GPU you are intending to put in there you will get better advice. Some older AMD cards will not work well at the moment (something to do with the fglrx driver but not au fait with that, others are)  while others will be fine.

As I say, with the lack of info that is about all I can say. When posting here, pays to give as much info as you can about your support issue. That helps us help you. You might like to have a read of the first, pink link in my signature at the bottom of this post for posting tips that will speed up support. :)

---

### Post by Autodave on 2017-05-23
Assuming that you are putting a PCIe card in, all you need to do (usually) is install the card and turn the PC on. The new card will be recognized as a video card and the on-board will be ignored.

---

### Post by Yellow Pasque on 2017-05-23
If you're talking about a laptop with switchable graphics: [https://ubuntuforums.org/showthread.php?t=2361610&p=13646812#post13646812](https://ubuntuforums.org/showthread.php?t=2361610&p=13646812#post13646812)

---

### Post by slickymaster on 2017-05-25
*Thread moved to **Hardware**.*

---

### Post by heron1337 on 2017-05-26
> **Bucky Ball said:**
> You don't give much information about the AMD card you're looking at or your machine so this is it. Put the card in, switch the machine on, go to 'Additional Drivers' and see if there is a driver for the card or it 'just works' and the driver is in the kernel. You may need to go into BIOS and switch off the internal graphics (if you find an option to do that). 

With details of the GPU you are intending to put in there you will get better advice. Some older AMD cards will not work well at the moment (something to do with the fglrx driver but not au fait with that, others are)  while others will be fine.

As I say, with the lack of info that is about all I can say. When posting here, pays to give as much info as you can about your support issue. That helps us help you. You might like to have a read of the first, pink link in my signature at the bottom of this post for posting tips that will speed up support. :)

i have amd r5 m330 and and obviously second intel card i tried using additional drivers but it not found amd card i also tried tihs command in terminal ,,glxinfo | grep OpenGL  and found this 

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 5500 (Broadwell GT2) 
OpenGL core profile version string: 4.3 (Core Profile) Mesa 12.0.6
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 12.0.6
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

---

