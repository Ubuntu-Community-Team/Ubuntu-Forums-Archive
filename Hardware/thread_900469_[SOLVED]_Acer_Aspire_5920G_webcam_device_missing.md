---
title: "[SOLVED] Acer Aspire 5920G webcam device missing?"
date: 2008-08-25
forum: Hardware
---

### Post by Golindo on 2008-08-25
To start this off so that you know, I am a complete lunix newbie. I know how to do most things in the GUI and a few commands. 

The prolem is as the title states, the webcam device seems to be missing. I was going to try it today after using Ubuntu for a couple of weeks, so I installed Camorama webcam viewer. The message I get is: "Could not connect to device(/dev/video0/). Please check connection." (also tried Cheese)

So due to my lack of linux knowledge I searched around a bit and found people with a little similar problems, but not the exact same. However I did end up installing (reinstalling aparently) a driver package called UVC. Latest revision btw. And as far as I could see in their supported hardware list, my laptop was included.
I decided to check the /dev folder and found the video0 file, however that is completely blank. 0 bytes.

Im completely lost here so any help would be appreciated. And if its complicated, please explain a little bit and not just say do this do that etc.

Thanks for reading.

PS: Using 8.04

---

### Post by newmath047 on 2008-08-25
try to reinstall webcam drivers

---

### Post by Golindo on 2008-08-25
That seemed to do the trick for Cheezy and aMSN but not for Camorama. Good enough for me hehe.

What I did: Open Synaptic Package Manager, search for driver. check EVERY SINGLE x server driver thats installed for reinstall. Reboot.

---

