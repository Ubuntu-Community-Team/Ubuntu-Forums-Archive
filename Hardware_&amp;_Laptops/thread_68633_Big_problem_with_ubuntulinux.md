---
title: "Big problem with ubuntu/linux"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by amplifier on 2005-09-23
I have a 700 MHZ Celeron, 256 MB of ram. I installed ubuntu twice to get to a black screen where it just hangs (right when the login screen should come up). I eventually got angry and installed SUSE to see if I would encounter the same problem. I was able to go into the gui in suse, but whenever I touch ANYTHING to do with video or information about the video card it goes to the black screen. I also have tried another video card (Hercules 3d prophet 4000xt). Same problem. I also have installed the nvidia drivers, but they have done nothing. Any ideas?

---

### Post by Gezzer on 2005-09-25
install via synaptic 
nvidia-glx

To enable the driver, run in a terminal
sudo nvidia-glx-config enable

---

