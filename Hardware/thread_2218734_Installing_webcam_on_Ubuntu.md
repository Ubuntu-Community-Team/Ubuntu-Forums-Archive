---
title: "Installing webcam on Ubuntu?"
date: 2014-04-21
forum: Hardware
---

### Post by terry14 on 2014-04-21
Hi there. I'm new to Ubuntu (and these forums). I recently decided to repurpose an old laptop which I want to use exclusively for skype. The problem is, my webcam doesn't seem to be working. It's an old Acer Aspire One and the webcam is an Acer CrystalEye camera. I googled around and saw suggestions to install an application called 'cheese' and after getting it on my machine, it seems to not detect any webcams. I'm positive the webcam itself is not damaged either since it was working on the windows install I had prior (which I sadly decided to wipe for this fresh install!).

So how can I get it working? Can you walk me through it step by step? I'm very new to linux and ubuntu but I can follow instructions :) Also, I am currently using the latest version, 14.04.

---

### Post by mastablasta on 2014-04-22
first you need to see if system recognised the camera. try lsusb or lspci commands and see if it finds it. if it doesn't recognise it it means drivers are missing. in that case you will have two possibilities - one is to find closed source drivers for camera or find the chip camera uses and make drivers for that chip work with your camera. if both fail then it means it's a windows only camera.

the fact that cheese doesn't recognise it is not a good omen...

---

