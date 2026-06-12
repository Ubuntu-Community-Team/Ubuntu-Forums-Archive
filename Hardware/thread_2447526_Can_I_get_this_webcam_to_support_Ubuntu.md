---
title: "Can I get this webcam to support Ubuntu?"
date: 2020-07-20
forum: Hardware
---

### Post by branperr on 2020-07-20
Hi everyone,

Apologies if this is the wrong place or breaks any community norms, I'm new to the forums.

I bought [this webcam ]("https://smile.amazon.com/gp/product/B088CQWPY1/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1")a few weeks ago when I was using Windows 10 since my built in webcam barely functions. However, I discovered when I transitioned to Ubuntu that my computer isn't detecting it. When I looked on the Amazon page, it states that it supports Windows and Mac, but doesn't mention Linux. Are there any drivers or anything that I can install that would allow me to use it? 

Thanks,

---

### Post by TheFu on 2020-07-21
> Are there any drivers or anything that I can install
That's a loaded question without any real data.
Certainly, the kernel you currently run doesn't automatically find drivers for that device (probably 2 devices - the video and the microphone).  So you need to determine what those are.  But this will always be a hassle going forward, so my recommendation is to return the device and buy a know-to-work webcam like a Logitech C270 for about the same price or a Logitech C920 Pro for 3x more.  These are both plug and use for every OS now.  
The C270 (720p resolution) is OOS most places, but Logitech has an order page with shipping in 1-2 weeks. A friend bought a few.
The C920 Pro (1080 resolution) is what I have. the last 5 yrs or so, it has been plug-in-use on Linux.  Almost always, I reduce the resolution to 720p, so if I were buying today, I'd get a C270 instead unless everyone on your video conferences has GigE WAN connections.

The audio for both is very reasonable for the devices, though better audio is possible if you are in a more professional or podcasting is the goal.  But lots of youtube vloggers use just the C270 and audio it provides happily.

With all that said, how much fighting are you willing to do to use that specific device?  Every kernel update (about 2x a month), you may need to manually rebuild the driver, if one exists, again.

Anyway, the first step is to determine the USB device number. Use **lsusb** to find that and websearch for existing driver support.  Many have none.  If you are a C programmer, you might be able to find a related webcam set of drivers, modify those, build them, install in the correct location, modprobe to load the module into the kernel, hook up udev for the new devices, plug in the camera and maybe it will work with V4L2 libraries.

As I said above, I'd return it and get a C270.

---

