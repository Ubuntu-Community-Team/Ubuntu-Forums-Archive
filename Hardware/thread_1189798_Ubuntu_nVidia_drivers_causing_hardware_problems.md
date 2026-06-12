---
title: "Ubuntu nVidia drivers causing hardware problems"
date: 2009-06-17
forum: Hardware
---

### Post by obiwankamote on 2009-06-17
Hi guys,

I have an HP Pavilion DV2725TX with an nVidia Gefore 8400M GS. I used to have Intrepid Ibex and after some time using it, my graphics card got busted. The tech support at HP said that the video card overheated. This happened twice and in both instances, it was when I had Ubuntu installed and the PC rebooted while I was using Ubuntu. The next time it booted, there was already a problem with the hardware.

Currently, I'm using Vista and it never had any problems. I saw this happening again when I used a USB based Ubuntu installation and saw signs of the problem when shutting down. 

I was wondering if anyone had a similar experience. Right now I'm thinking it's because of the Ubuntu nVidia drivers? Anyone got any ideas? :)

---

### Post by overdrank on 2009-06-17
I am using the nvidia drivers 185.xx on my nvidia 8200m on HP G60 no issues what so ever for over a month. :)

---

### Post by recluce on 2009-06-17
> **obiwankamote said:**
> Hi guys,

I have an HP Pavilion DV2725TX with an nVidia Gefore 8400M GS. I used to have Intrepid Ibex and after some time using it, my graphics card got busted. The tech support at HP said that the video card overheated. This happened twice and in both instances, it was when I had Ubuntu installed and the PC rebooted while I was using Ubuntu. The next time it booted, there was already a problem with the hardware.

Currently, I'm using Vista and it never had any problems. I saw this happening again when I used a USB based Ubuntu installation and saw signs of the problem when shutting down. 

I was wondering if anyone had a similar experience. Right now I'm thinking it's because of the Ubuntu nVidia drivers? Anyone got any ideas? :)

Google for "nVidia heat issue" and you will learn that there is a design flaw in your Gefore 8400 chip that will cause it to prematurely die because of heat issues.

That your notebook died under Ubuntu is probably just pure bad luck - especially if you use the Nvidia Proprietary drivers, as you are essentially using the same graphics drivers under Ubuntu and Vista at this point.

There is no solution to the nVdida heat problem, except a couple of workarounds:

- improved warranty (Dell for example, extends the warranty on notebooks with this problem, at least in many cases)
- BIOS update with lower threshold temperature for the fan(s) (Dell does that, but it makes your notebook noisier)
- other fan control tool to run fans earlier/faster (again more noise)

---

