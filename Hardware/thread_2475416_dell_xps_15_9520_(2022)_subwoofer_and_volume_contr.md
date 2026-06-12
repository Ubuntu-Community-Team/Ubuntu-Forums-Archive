---
title: "dell xps 15 9520 (2022) subwoofer and volume control not working plus battery life"
date: 2022-05-26
forum: Hardware
---

### Post by kdvr81 on 2022-05-26
I've just received my new work laptop a Dell XPS 15 9520 (2022) and have two issues I can't seem to resolve properly.
So, I was hoping the community could give me some tips, maybe an older model has some insights on how to solve.

My first obvious issue is with the speakers (sound). They sound really flat thin and soft. So I have been trying to fix and got as far as [using this guide]("https://davidwpearson.wordpress.com/2020/01/10/lenovo-laptop-subwoofers-and-linux/#fix") to solve the problem. 
In short I had to use HDAJackRetask to override a pin connection to enable the sub-woofers. It feels like this is a kernel issue which has been patched for previous models. [Found a repo that describes the issue]("https://github.com/kristinpaget/xps-15-9510-audio")
Now, I would love to try and open a patch for this model, but to be honest I have no idea on how to find out what to put there and how to test the patch. So my work around with the guide is my best bet at the moment.

The problem now is though, the sound is great but I can't control the volume, it is either blasting at 11 or completely off. 
Hopefully someone has an idea on how I might be able to solve the volume control.

My second issue is with power management. I had charged the laptop to 100%, closed the laptop over night and this morning it was completely drained.
Again, I'm hoping someone might have some tips here.

All of the rest works perfectly, but battery and sound are pretty crucial (to me) so I'm crossing my fingers that someone might be able to help me out.

Now a couple of things:

- I'm running Pop!_OS 22.04 LTS but had similar issues with Ubuntu 22.04 LTS so that's why I posted it here. 
- The laptop is brand new and except for the workaround I haven't done anything else to the system
- The volume is perfectly controllable using a headphone

Anything I can do to provide more information  I can do, I consider myself pretty confident with Linux.


Update: I've noticed I do have an option to select "Analog Stereo 2.1" from the sound panel. When I click the subwoofer it works and the volume is gradually adjustable HOWEVER, when I play music the subwoofer isn't used and the sound is terrible. Only Analog Stereo Output works with the broken volume slider.


Update 2: If I go in to sounds, I can gradually change the volume for each application, but system volume does not change all the volumes

---

### Post by steve-boardwell on 2022-07-11
It is a bug/missing tweak in the kernel - I've filed a cherry pick bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1981364](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1981364)

---

