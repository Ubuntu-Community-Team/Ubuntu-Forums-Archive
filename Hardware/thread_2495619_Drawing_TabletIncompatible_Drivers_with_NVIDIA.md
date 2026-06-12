---
title: "Drawing Tablet/Incompatible Drivers with NVIDIA"
date: 2024-02-25
forum: Hardware
---

### Post by jsaf on 2024-02-25
I have an ASUS ROG RTX 3060, and I am trying to pair a Huion Kamvas 13 with it. I am running Ubuntu 22.04 Desktop. 

I realized that after installing NVIDIA driver 535 that the tablet would extend the main screen display from the HDMI port but before that there was no signal with the open source GPU driver. It appears by trial and error that the GPU is only attached to the HDMI for streaming displays on my laptop and not USB. It works with the Huion driver on Windows having NVIDIA but not for Linux using a dual installation, it's the same GPU. I've also tried manually mapping the pen stylus with no success. So I have double, triple checked my Huion driver selection, used the methods described for installing it, and the app will load itself, but there's no connection to the driver control while the screen is illuminated. So the response of the tablet to the installation of the Huion driver makes me think that I need a driver comparable to that on my Windows that works with data/input from the tablet, or there's some other gap in my steps to making the driver work. Any advise on what NVIDIA driver should work with the Huion or other option to get the device to run?

I did download git input-re-mapper per another discussion but I have no clue how to map a pen to a tablet with right proportions. I'd rather use the Huion driver. My main cause for using the tool on Linux is that Linux is more stable and appears to render more smoothly any drawings.

---

