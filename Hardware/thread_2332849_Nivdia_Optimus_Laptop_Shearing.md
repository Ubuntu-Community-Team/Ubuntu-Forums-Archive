---
title: "Nivdia Optimus Laptop Shearing"
date: 2016-08-04
forum: Hardware
---

### Post by Mr. Universe on 2016-08-04
I have an MSI GE70 with an 860M that I got in November 2015. I failed to do enough research before getting it and it is cursed with "Nvidia Optimus". I've been struggling with it since then. I currently just use Nvidia PRIME to switch GPUs when I need the discrete card but mostly just use the integrated one. When I do use the Nvidia GPU I encounter massive shearing in everyday tasks(I've attached pictures of the screen when it happens. Screenshots don't work). From what I can't tell it is a problem with the GPU not correctly redrawing the screen after a change. 

I'm not huge into games so the lack of GPU power hasn't been to big of a problem. I recently started getting into Vulkan development and the Haswell based integrated GPU I have doesn't have Vulkan support. So I'm trying to use the Nvida card but the tearing and half draw updates makes development impossible.

There is no way to disable the integrated GPU in BIOS. I'm running Ubuntu 14.04. I currently am using the 367.35 Nvidia driver but I've had this problem on every version. Is there anything I can do to fix this? I would guess Xorg might have something to do with, would running 16.04 with the Mir preview be worth trying?

My System:
Laptop: MSI GE70 Apache Pro 12
OS:     Ubuntu 14.04
CPU:     i7-4700HQ 2.4-3.4 GHz
RAM:     16Gb
GPU:     GTX 860M 2Gb

---

### Post by grahammechanical on 2016-08-04
Forget Mir.

Mir & Unity 8 go together and although Mir itself might be up to standard Unity 8 is far from being a desktop user interface replacement for Unity 7.

Those who have had the most success in getting a loaded Unity 8 are those with Intel graphics. We cannot use proprietary video drivers and there seems to be some problem with Nvidia adapters even when using Nouveau.

I have an Nvidia GT220 and when I switch to Unity 8 I get a background wallpaper with Unity partially loaded and the mouse point fixed centre screen. It is a complete GPU lock up. I get this on both 16.04 and 16.10 (under development). I would be glad for a little screen tearing.

There is another issue. To use X apps on Unity 8 we need to install something called Libertine. It will install and run an X app in a Linux container. For those who are able to get a Unity 8 session loading then Libertine will also work but, it is under massive development and breaks frequently. There are several threads about Unity 8 & Libertine in the Ubuntu Development section of the forum.

You could try dual booting with 16.04 and then test it out to see if the X Server version and kernel work better than the 14.04 set up. What you will not have with the Unity 8 session is any means to switch from Intel to Nvidia because you will not be using an Nvidia driver.

Regards.

---

### Post by Mr. Universe on 2016-08-04
Alright, so Mir is out as a solution.

I am wanting to update to 16.04 in the near future. Have there been any kernel changes that have helped? Or are there any avenues to explore?

---

### Post by Mr. Universe on 2016-08-10
I just finished installing 16.04.1 on the laptop and the 361 Nvidia drivers(which seem to be the recommended version). The shearing issue is still there. 

I'm out of ideas for getting the Nvidia card to work well for everything. I'm going to look into setting up bumblebee and trying that again. Last time it didn't work so well for me.

---

