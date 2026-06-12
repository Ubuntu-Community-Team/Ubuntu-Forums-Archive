---
title: "problem with new NVIDIA driver version 180"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by DAllenSmith on 2009-03-29
i just updated to nvidia version 180 and when i did a reboot everything seemed to work fine up untill after i enter my user name and password, it just went blank, the laptop screen didnt turn black, it shut off completely, the startup sound carried on and everything seemed to be working but the screen just went off, what could be wrong?
I am using ubuntu 8.10 x86 
HP pavilion dv6604nv

any other info u might need just let me know and ill be prompt to getting it up here

---

### Post by cariboo on 2009-03-29
For some reason your resolution has been set to something the display can't handle, If you have another computer you can use remote desktop to go in and change the resolution to something the display can handle.

Jim

---

### Post by DAllenSmith on 2009-03-29
there surely must be another way, that is just silly

---

### Post by infoseeker on 2009-03-29
Does booting into 'recovery mode' work ok?

---

### Post by DAllenSmith on 2009-03-29
yeah that works, i do that and do the fix x server thing and thats how i get back with being able to see then i have to set the hardware drivers to version 177 or 173 and then reboot again

---

### Post by norwoods on 2009-03-29
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by Bri10 on 2009-04-02
I have the same problem!

I found out that it was switching to the vga/tv out on startup! Scrolling through the screens (func-f4) gets the laptop screen back on.

I haven't seen any solutions to this yet though?

---

### Post by DAllenSmith on 2009-04-03
alright i never solved this but here is what i did.

since juanty is being released i decided to just install it since i messed with this so much that i couldnt even get ver 177 to work anymore. seeing that i have my /home on another partition i figured this was the quickest and easiest solution. so i downloaded the beta 9.04 burned it and installed it. installed all the updates and then activated the 180 version. this seems to work fine now, at first i couldnt use ubuntu screen resolution app to change the res so i had to use nvidias X server settings. then after a while though for some reason it let me do it in the system sreen res app. i know this shouldnt be the way to fix things but actually this was the quickest way to solve it after spending 2 days trying to figure it out, going this route had it solved and my full res back to normal in 35 min. plus ext4 is very nice and i dont care what anyone says i can def feel a difference. so if u have your home on another partition and dont mind reinstalling your apps then do this, all the settings for your apps will be restored once u reinstall them

---

