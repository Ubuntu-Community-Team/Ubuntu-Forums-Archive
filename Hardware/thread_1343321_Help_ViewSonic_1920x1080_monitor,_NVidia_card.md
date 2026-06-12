---
title: "Help: ViewSonic 1920x1080 monitor, NVidia card"
date: 2009-12-01
forum: Hardware
---

### Post by xav on 2009-12-01
I've been running Ubuntu for years quite happily on an Acer monitor that does 1280x1024, but decided I needed a bit more space for my Inkscape work, so I bought a ViewSonic VX2260WM with a native resolution of 1920x1080.

When I boot the machine I get the splash screen running at 1024x768, but when it tries to switch to the login screen, I get an "out of range" error on the monitor, which then switches to standby.

I'm using an NVidia graphics card, which was cheap when I bought it a few years ago, but which has been good enough to use Compiz on the old Acer monitor. It's identified in the Xorg log file as a "GeForce FX 5200 (NV34)" with 256MB of RAM. I'm using the "NVIDIA accelerated graphics driver (version 173) [recommended]" as reported in the Hardware Drivers app.

If I delete the xorg.conf file completely I can get to a login screen and then to a desktop, running at 1024x768. When I try to run nvidia-settings it tells me I'm not using the NVidia driver and that I should run "nvidia-xconfig" as root to fix that. If I do that, I'm back to getting an "out of range" error at the login screen until I delete the xorg.conf file and restart X again.

I've tried running "gtf 1920 1080 60" and putting the output into the xorg.conf file following a few posts I found online, but still no luck.


I suppose the first question is whether my graphics card is just too old and/or rubbish to handle this resolution? If it's not, and I should be able to get 1920x1080 with this card, any tips on how to achieve it?

I've attached a zip of my latest Xorg log file - but this is from a boot with no xorg.conf so that I could log in at 1024x768 to post this message.

Any help or suggestions would be greatly appreciated before my eyes start to bleed from having to look at the huge, fuzzy pixels that 1024x768 brings ;)

---

### Post by xav on 2009-12-02
An update on this issue.

By poking the xorg.conf file enough, I was able to get the machine to boot to 1024x768 using the NVidia driver, which then let me run nvidia-settings.

Nvidia-settings seems to think that the native resolution of the panel is 1600x1200, rather than the 1920x1080 that it should be. If I set it to use any resolution higher than 1280x1024 I get red and green flickering lines, starting at the left of the screen and extending up to halfway across the monitor, depending on the resolution I pick.

Any suggestions about getting it to 1920x1080? And what about the flickering lines - are they evidence that my graphics card isn't up to the task of going that high, or is it likely to be something else?

Any help would be greatly appreciated.

---

### Post by xav on 2009-12-02
More poking, more Googling, and it looks like it is the graphics card that's the problem.

I tried the screen with a Dell Mini 9 Netbook running UNR and was able to configure it to its native resolution. That was via the analogue (VGA) connection on the netbook, so I figured I'd try the VGA connection on the graphics card instead of the DVI one.

It turns out that while the VGA port will happily drive it at its full resolution, the DVI port on this old, cheap card maxes out before then. So now I've got it running on the VGA connection, and I'm weighing up whether I want to buy a new graphics card, or if it's just time to replace this 5-year-old machine anyway ;)

---

### Post by Jackelope King on 2009-12-02
NVidia and ViewSonic just don't seem to get along well. I plug my HP Pavilion dv3501n into my VieweSonic Q19wb-2 to use it more like a desktop when I'm at home, and the NVidia control center just can't seem to read the EID information from the monitor and allow the correct resolution displays. It works just fine at whatever resolution I set when I use it for presentations with projectors, but this ViewSonic monitor just seems to bewilder NVidia.

The next monitor I buy definitely will NOT be a ViewSonic.

Sorry I can't offer more help. I've been struggling with this myself ever since I got this machine over the summer.

---

