---
title: "Help!! Graphics lost."
date: 2008-12-21
forum: Hardware
---

### Post by arielt1985 on 2008-12-21
Hi everyone,
Just moved to Ubuntu and got lost very quickly...
I tried to get the Visual Effects to work, failed, and now I'm experiencing the following problems:

1. Movie playback lost. I'm trying to play the Experience_Ubuntu.ogg file, which worked fine when I just installed ubuntu. I can hear the soundtrack but no image is displayed.

2. Visual Effects don't work. This is quite despressing since I don't know where to begin. What do I have to do to check which configuration isn't right. How do I find out if my driver is up to date? What else can I do to debug this problem. I must say that there are several tutorials on this subject and even specific ones for my card, but following them just seemed to get things worst... :(

My graphics card is: ATI Mobility Radeon M6 LY, (works fine in windows), on an ThinkPad X32 laptop. I just installed Ubuntu 8.10.

Thanks in advance for any help.
Ariel

---

### Post by bdoe on 2008-12-21
When you tried to enable desktop effects, did it mention anything about needing to install the ATI Restricted drivers?

It sounds like something got borked pretty good when you enabled desktop effects (which are provided by Compiz, a screen compositing manager, which requires the restricted 3D drivers to work). Try disabling desktop effects, then go to System -> Administration -> Hardware Drivers and see if the ATI restricted driver is enabled or not. Post back with the results.

---

