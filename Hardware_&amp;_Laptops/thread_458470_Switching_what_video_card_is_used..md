---
title: "Switching what video card is used."
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by SmoshySmosh on 2007-05-29
In my computer I have two video cards (I guess you can say) One intergraded, and one in my PCI express slot. When I install Ubuntu and then install the restricted drivers (Which from my knowledge is a easy way to install my nvidia drivers) it installs Nvidia-glx, and from what I know I need nvidia-glx-new because the card I want to use is a Nvidia Geforce 7600 GT OC. Also after the drivers are installed, I go to the system hardware log where it shows everything, and check my video card. It does not give me any informaton like 256mb/PCI Express etc, It just says unknown. So now I am kind of stumped, How do I fix this?

---

### Post by Blender on 2007-05-29
Could you post the contents of **/etc/X11/xorg.conf** and **/var/log/Xorg.0.log**?
And also the output of the commands **dmesg**, **glxinfo** and **lspci**.

---

### Post by SmoshySmosh on 2007-06-01
Sorry this took so long, I had to reformat my whole PC then go on a school trip, I am about to install Ubuntu on a 30gig partition I made this time around, Can you please give me a step by step guide on how to install the drivers for my Nvidia 7600 GT OC, so I can go ahead and get my Ubuntu setup. Also I am looking for pointers and other information that will make my setup go as smooth as possible, if anyone has pointers.

---

