---
title: "yet another 8800 gts driver problem"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by Toast2120 on 2009-04-13
Hey all! Good to be here. Been using Ubuntu for years, but this is the first time I'll be getting those video drivers to work. Word is Steam looks GREAT on Linux. I'm currently using a different PC to access the internet, because, well, Kubuntu isn't looking so hot right now. Here's my problem. 

Installed Kubuntu fine. Did updates. Security. Drivers. All fine. But after I restarted my PC, I now only have a command line login, no GUI. It says
"Aperture pointing to e280 RAM. Ignoring."
"Your BIOS doesn't leave a aperture memory hole"
"Please enable the IOMMU option in the BIOS setup" I dont have one
"This costs you 64 MB of RAM"
"kinit: name_to_dev_t(" image name
"kinit: trying to resume from..." image name
"kinit: No resume image, doing normal boot..."
"cheese login"

Yes my PC is named cheese. Anywho...

My rig is a AMD 4200 64 bit Dual Core 2.21 GHz; SLI 8800 GTS 512 RAM; 4 GB RAM; rest is pretty generic

I'm thinking the nVidia drivers wrote over my boot image or something, but I have no idea where to go now. Using 8.10. I could go to regular Ubuntu if I had to. Just did Kubuntu cause that would mean I wouldn't have to go and find all my necessary drivers.

The only other problem I have to say is that during the live cd and install the screen kept flashing every few seconds, but it stopped after I installed the video drivers. But I had to restart and well... that's where I am at.

I installed the nVidia drivers via GUI, NOT command line, so that might be a problem.

On a last note: not trying to be mean, rude, or ignorant... but why does this spell check consider "Ubuntu" to NOT be a word by default. Just curious.

---

### Post by inobe on 2009-04-14
welcome

assuming if you have onboard video please disable it in the bios, also make sure the vga cable is plugged into the gts card and not the onboard video.


edit: to add, also make sure your plugged into the correct card or disable sli.

---

