---
title: "VMware and video card"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by mits on 2007-03-01
Hi I am new to the forum and the Linux, too. I have installed Ubuntu in VMware in Windows XP machine and I am thrilled with that. My question is this: Is it possible to see my actual video card from VMware (not the software card VMware uses) so I'll be able to install drivers and have actual 3D acceleration or do I have to make an actual dual-boot system?
I have an nvidia 6800 video card.
Thanks in advance.

---

### Post by markr on 2007-03-01
Welcome,

VMWARE isolates the OS from the hardware in order to make it completely generic (i.e. you can take the image to any PC and run it.

This has the downside that you can't communicate directly with your graphics card and so can't have acceleration, sorry.

You will have to dual-boot and install the nvidia drivers to get true acceleration and the ability to use opengl/compiz/beryl etc.

Creatin a dual-boot system is very straight forward, and will give you the ability to see linux running at full speed (not slowed down by vmware emulation),  I'm sure you'll never look back.

Mark.

---

