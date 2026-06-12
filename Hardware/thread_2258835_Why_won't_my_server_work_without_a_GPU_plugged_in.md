---
title: "Why won't my server work without a GPU plugged in?"
date: 2014-12-30
forum: Hardware
---

### Post by josh111 on 2014-12-30
Hi! I just installed Ubuntu Server and since the installing was done, I thought I could remove my nice R9 270x from the sempron server.  For some reason when I rebooted the system without the GPU, I couldn't connect via PuTTY or even access files from Windows. So I plugged the GPU back in, and everything works again. What can I do to make it work without a GPU. I don't want the added power cost of a GPU for a simple file server. Thanks a bunch in advance!

---

### Post by Reha_Andrew on 2014-12-30
Boot the server in text mode.  Try video adapter

---

### Post by josh111 on 2014-12-31
> **Reha_Andrew said:**
> Boot the server in text mode.  Try video adapter
How do I do either of those? Sorry, I am really new to Ubuntu Server! Thanks for the response!

---

### Post by kpatz on 2014-12-31
Ubuntu Server is always in text mode unless you install a GUI desktop manager.

When you say GPU, are you referring to an on-board video chip on the motherboard, or a video card?  PCs won't boot without some sort of video adapter available.  No monitor needs to be connected, but the video adapter has to be there.  If the motherboard doesn't have on-board video, a video card needs to be present.

The power usage of a GPU in text mode is minimal, but if you want to conserve power, get a cheap basic video card and put that in.  If it's onboard video, look in the BIOS settings to see if there's a basic "Intel video" option that turns off the faster GPU.

---

### Post by josh111 on 2014-12-31
> **kpatz said:**
> Ubuntu Server is always in text mode unless you install a GUI desktop manager.

When you say GPU, are you referring to an on-board video chip on the motherboard, or a video card?  PCs won't boot without some sort of video adapter available.  No monitor needs to be connected, but the video adapter has to be there.  If the motherboard doesn't have on-board video, a video card needs to be present.

The power usage of a GPU in text mode is minimal, but if you want to conserve power, get a cheap basic video card and put that in.  If it's onboard video, look in the BIOS settings to see if there's a basic "Intel video" option that turns off the faster GPU.
Yea it doesn't have onboard video so I guess I will have to find some cheap GPU to throw in there. Thanks!

---

