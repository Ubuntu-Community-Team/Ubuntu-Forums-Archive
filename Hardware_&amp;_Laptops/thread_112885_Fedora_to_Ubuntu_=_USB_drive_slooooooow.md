---
title: "Fedora to Ubuntu = USB drive slooooooow"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by dangermouse28 on 2006-01-05
I've recently switched from Fedora to Ubuntu and hit a problem. Before wiping Fedora I backed up all my fonts and several large video files to my USB drive. Switched to Ubuntu and tried to copy all the stuff back over - BAD IDEA. I gave up after 15 mins, and 94 font files. The CPU was running at 100% the whole time as well. Googled around and tried to set the dma on, but got

HDIO_SET_DMA failed: Invalid argument

For what it's worth, I'm using an HP ZD7000 laptop which has USB 2 ports so it's not that. Any ideas anyone?

---

### Post by Amon_Re on 2006-01-05
[QUOTE=dangermouse28]I've recently switched from Fedora to Ubuntu and hit a problem. Before wiping Fedora I backed up all my fonts and several large video files to my USB drive. Switched to Ubuntu and tried to copy all the stuff back over - BAD IDEA. I gave up after 15 mins, and 94 font files. The CPU was running at 100% the whole time as well. Googled around and tried to set the dma on, but got

HDIO_SET_DMA failed: Invalid argument

For what it's worth, I'm using an HP ZD7000 laptop which has USB 2 ports so it's not that. Any ideas anyone?[/QUOTE]

What do you get as a result for the following commands:

sudo dmesg | grep "usb"
lsmod

---

### Post by dangermouse28 on 2006-01-06
I thought of that - I get the "high speed" usb connection. 

I think I've solved it - I tried copying across using the terminal and 7000 fonts shot over in under 2 mins - no problem. I then realised that I was running whatever the default video driver is supplied on CD. Could be that the CPU was working on 7000 odd font previews in nautilus while transferring files? I'll install the pukka nvidia driver today and see if that sorts it out.

---

### Post by dangermouse28 on 2006-01-13
Update - installing the newest nvidia driver worked a treat - normal service resumes!

---

