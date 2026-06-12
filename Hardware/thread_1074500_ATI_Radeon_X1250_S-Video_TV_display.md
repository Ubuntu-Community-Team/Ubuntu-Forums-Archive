---
title: "ATI Radeon X1250 S-Video TV display"
date: 2009-02-19
forum: Hardware
---

### Post by cybermitten on 2009-02-19
Hi everyone-
 I'm a relatively new user, and just installed Ubuntu and Kubuntu desktop on an ACER laptop after getting sick of VISTA. Everything is going smoothly except for Network issues in Kubuntu (which I will post in the Network area) and a video problem under buth Ubuntu and Kubuntu.

 The issue is that I can't get the S-Video out to display correctly. My goal is to get it set up so that I can display video Fullscreen on my TV from the Laptop, but what I get is this:

1. When using the built in drivers- No detection or output to TV
2. When Activating the Proprietary ATI drivers- Desktop is only partly displayed- I lose a bit of the screen top to bottom and a large portion to either side.

-I have tried using Envy, with no improvement.
-I have tried using aticonfig to set the relative width and height, but this only shrinks the amount of the TV screen that is used, the ammount of the desktop/video that displays remains cut off.
-I have tried changing the resolution for the TV. Any atempt to change resolution blanks out both displays, and requires a reboot under restoration mode with the TV disconnected to get my desktop back.
-Clone mode is the only way I can activate the TV display in Catalyst. Extended desktop gives a blank display on both screens after the required reboot.
-I tried manually configuring the TV screen in xorg.conf, this crashed out on reboot and required I remove the changes in recovery mode to get things running again

The specifications of my system are:
-ACER Extensa 4420, AMD64 dual Core, 3Gig Ram
    Display adapter is:
        ATI Radeon X1250 on board with S-Video out
     TV is an old RCA 23inch. Using Composite video (S-Video to composite adapter connected to ATI Radeon S-Video out, works under windows)

  I am using VLC as the video player (needed something I could set to X11 output to prevent flicker- looks great on the laptop)

My goal is to get videos to the TV, I don't care if the desktop itself is properly displayed to the TV, I just need good video.

I've searched through the forums, but have only found the above fixes that I've tried and failed at. Does anyone have any advice on how I can accomp[lish full screen video to the TV?

Thanks

---

### Post by seventhsamurai on 2010-01-28
I have the exact, same notebook as you do - Acer Extensa 4420. But I haven't been able to even configure any ATI drivers.

I am a very, very new Linux user and switched just a couple of days ago from Winblows. I love Ubuntu. Everything is working like a peach except for my inability to enable the S-Video TV output.

Been trying all sorts of stuff from online forums. The first time, it asked me to download some ATI drivers. I followed instructions, and when I rebooted, I could never get to the desktop. It took me straight to the prompt. None of the online tips and tricks to fix this issue and get back to normal worked. I just ended up reinstalling Ubuntu.

Next time, I attempted the Envy option. Same result.

Someone please, please help!

---

### Post by silo4321 on 2010-02-01
I have an LG laptop with the same x1250 video card. The S-video worked with the proprietary drivers but were discontinued at catalyst 9.3 and last worked in the Intrepid Ibex release. So you are now stuck using the radeon driver unless you use an old release of Ubuntu.

I managed to get S-video working in Karmic Koala though. The only output issue I have is a small green line at the bottom of the screen

Not sure if this works for everyone but it worked for me.

You need to edit your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

Add this to the Device section

> Option "ATOMTvOut" "TRUE"

---

