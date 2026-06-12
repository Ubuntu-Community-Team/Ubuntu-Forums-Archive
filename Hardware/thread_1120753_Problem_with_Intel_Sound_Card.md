---
title: "Problem with Intel Sound Card"
date: 2009-04-09
forum: Hardware
---

### Post by vijay.soragudi on 2009-04-09
Hi,
I am using Lenovo notebook. It has an Intel sound card installed. It is not working in ubuntu. Can any one please help me sort this out?

---

### Post by chessnerd on 2009-04-09
Find out what type of sound card you have (either get your laptop's manual, boot into Windows and go into the device manager (if you have a dual-boot setup), or put the name and model of your laptop in Google and find out what sound card it came with by default) after that you need to get the kernal module from Google (a code that usually will start with snd-, but this isn't alwasys the case). Then, open up a terminal and put in:
```
sudo modprobe (module)
```
See if any errors come up. If they don't, you might have found the right one. Load up alsamixer:
```
alsamixer
```
And if you can configure the sound, it should work. 
If you get an error you can try a different module.

I'm having trouble with a sound card myself at the moment (a Dynex DX-SC51). This didn't work for me, but it might work for you.

---

