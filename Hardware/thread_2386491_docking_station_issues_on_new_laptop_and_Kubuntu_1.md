---
title: "docking station issues on new laptop and Kubuntu 17.10"
date: 2018-03-06
forum: Hardware
---

### Post by TechnoJunky on 2018-03-06
I just got a new Dell Inspiron 15 5000 laptop with an Nvidia 1050.  I installed Kubuntu 17.10 and without the docking station, it works great.  I changed the video driver using the Driver Manager in System Settings to Nvidia (384.111).  I then downloaded the driver for the DisplayLink docking station (Dell Docking Station - USB 3.0 (D3100) ).  I compiled from source and rebooted and everything seemed fine except there's a square around my mouse on many screens.  It's hit or miss though if it shows up.  Sometimes it's there and blocking me from seeing the text I'm trying to type other times it's not.  Selecting text is a pain as the mouse square never lets me see if I've highlighted far enough.  I went to the DisplayLink site and found that they claim the Nvidia driver isn't supported  (Closed source AMD/NVIDIA drivers are incompatible with DisplayLink driver. Please use open-source AMD/NVIDIA drivers instead.)  So I went back to Device Manager and changed it back to Noveau.  Rebooted and now the laptop is slow as hell.  It takes 10 seconds or longer to see the K menu, then 10 seconds to see the results of what I click there, and then 10 for the next and so forth.  I rebooted but that didn't help.  I then opened the laptop lid and could see that the display is being mirrored between my external monitor and the laptop and oddly, if the lid is open, no delays.  Close the lid, everything takes 10 seconds or more, open works great.  I switched back to the Nvidia driver and no delays, but I have the square around the mouse.  Anyone have any tips or suggestions?

I originally chose the Nvidia driver because I've found many games don't work well (some not at all) with the Noveau driver.

---

### Post by droid2bsd88 on 2018-03-07
Have you tried grabbing the official nvidia driver from their site.

---

### Post by TechnoJunky on 2018-03-09
thanks for replying droid.  But I don't think the version of the nvidia driver is going to help, if they're saying the nvidia driver is incompatible.  What I'd like to try, and probably won't stay with, is getting the Noveau driver working properly.  This is what the DisplayLink company suggests.  So what I'm hoping to find here is someone that can help with this weird slowness when using it and keeping the laptop lid closed.

---

### Post by TechnoJunky on 2018-03-13
I suppose this can technically be marked as solved.  I've decided to return the docking station.  I'm not satisfied with it.  Since the laptop only has USB 3.x, it doesn't support receiving power thru the port, so I have to plug both the laptop in and the docking station.  Also when video goes thru the docking station it's significantly darker than just plugging the monitor into the HDMI port.  So for the past few days I've really only been using it as a glorified USB hub and it's way too expensive for that.

---

