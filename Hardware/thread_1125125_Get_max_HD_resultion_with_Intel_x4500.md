---
title: "Get max HD resultion with Intel x4500"
date: 2009-04-14
forum: Hardware
---

### Post by whitethunder on 2009-04-14
Hi All, 

I have recently installed Ubuntu 9.04 on a desktop which uses the intel graphic accelerator x4500. As I have read on the forum, a lot of people reported problems with the driver of this chip. Some people have written that the driver has been fixed however, I still can't get the maximum resolution (1920x1080) which I can get with my other desktop. That resolution does not even exist in the list of available resolutions, the maximum is 1680x1050. However, if I chose a resolution above 1024x768, the display gets messed up and I cannot fix it unless I connect the PC to my old monitor, then I can see some part of the display and I have to lower it back to 1024x768. 

Is there a fix for this? I thought Ubuntu 9.04 has fixed this problem but apparently it still exists. 

Thank you very much.

---

### Post by AvgUser on 2009-11-14
*bump*  Just installed 9.10 on new Biostar T41 mobo with Intel x4500 onboard video.  After installing restricted extras, the best available resolution is 800x600.  Is there a driver / config available to get this working?

---

### Post by SonicSteve on 2009-12-09
I have the same issue. Asus p5g41-m mainboard g4100 chipset. 800x600 resolution. I'm trying to find a fix also. So far there is very little on the net about linux and this chip.

What's interesting is that 3D seems to work, compiz is up and running but the Resolution is broken. This doesn't seem to be a big deal but no one seems to know what to do.

---

### Post by ST3ALTHPSYCH0 on 2009-12-09
Have you tried generating an xorg.conf file? I know that I've read a lot of issues with Intel GPUs, and I don't know if this would help any. Click the link in my sig to learn how to create a complete xorg.conf if you don't know how.

---

### Post by SonicSteve on 2009-12-09
I'll give a go tomorrow. Thanks

---

### Post by ST3ALTHPSYCH0 on 2009-12-10
Steve, are you still running Jaunty as it states in your profile? If so, you might benefit from reverting to an older driver. I found instructions [here](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) to revert to the Intrepid driver, and many people saw graphic improvements.
I don't know if this might help anyone in Karmic, nor do I know how to go about doing it even if it would.

---

### Post by SonicSteve on 2009-12-10
I'm testing it with Karmic 9.10. I haven't tried 9.04 yet perhaps I should. As for reverting the driver; I've done this before using jaunty, and I reverted to the 8.10 intrepid driver with limited improvements. Keep in mind that was using the intel x3100 chip. It's hard to say how this might turn out. I doubt that it would be any worse.

---

