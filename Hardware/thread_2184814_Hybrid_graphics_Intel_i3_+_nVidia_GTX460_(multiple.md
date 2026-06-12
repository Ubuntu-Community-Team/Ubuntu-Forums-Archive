---
title: "Hybrid graphics: Intel i3 + nVidia GTX460 (multiple monitors)"
date: 2013-10-30
forum: Hardware
---

### Post by mihai.nicolaescu12 on 2013-10-30
Hi, I'm trying to get Ubuntu to run with 4 screens the same way Windows does. A graphical representation of my current setup is shown in the attachment. I hope this post doesn't come off as shallow, but it's been years since I've been trying to wrap my head around this problem. Throughout the time I tried many different suggestions people had on different threads here, on other forums, IRC rooms, etc. Of course I even totaled my system countless times - in time I learned a few small tricks to help me recover it but I hope that this time, all of that will help me help you help me help us all :) Here's some basic info:

**Hardware**
Motherboard: Gigabyte H55M-UD2H
CPU: Intel i3 540, socket 1156, 3.06 GHz
GPU: nVidia Gigabyte GTX460 256-bit

**Software**
Linux: Ubuntu 12.04.3 x64
Kernel: 3.8
Driver: 304.88

This setup works for me in Windows when I set PEG as the primary display, and the IGP as "always on" (regardless of the existence of PEG). This way, Windows installs and uses both drivers (intel and nvidia), allowing me to configure every screen connected to either board. At the moment, I'm using PEG as the primary display and the IGP is set to "only if no PEG available", so that I can run Ubuntu on the 21.5" screen in the middle and mirror it on the 32" TV (I don't know if the names of those options are accurate, I could take pictures of the BIOS screens though and post them later).

I guess the reasonable thing to ask first is - is this even possible in Ubuntu? (I mean without any hardware changes). I've kinda lost hope here, but won't give up this time - I'll back everything up and and get ready to try anything you can think of. I can and will provide outputs for anything you ask, just please be specific - I'm not sure I'm even close to being an intermediate user yet (yes, even after so many years). 

I would definitely love to get it all running like in the attachment, but the screens on the nvidia card don't need to necessarily be mirrored (that setup makes more sense in Windows for games / movies). However I will also settle for just the primary screen - really, nothing else - just the main 21.5" running off the nVidia, knowing that if I really need all the screens, all I have to do is reboot and go Windows (without changing the settings in the BIOS). With both the IGP and the PEG active, Ubuntu loads the Intel driver and displays a mirrored image on the 17" side screens.

Well, I hope this whole thing makes some sense and thank you for at least having the patience to go through it - any help would be more than greatly appreciated.

---

