---
title: "D945GCLF2 mITX motherboard with S-video"
date: 2008-09-28
forum: Hardware
---

### Post by C.S.Cameron on 2008-09-28
I'm thinking of building another mini ITX system.
Intel has just released the D945GCLF2 mITX motherboard with  dual-core Atom and S-video.
My wifes D945GCLF works great for her computer needs. 
My daughters D201GLY2 mITX with SIS chipset sucks.
I understand there are issues with S-video and Intel graphics.
The board has GMA 950.
I'm wondering if anybody has gotten S-video working with this board or with GMA 950 in general.

---

### Post by C.S.Cameron on 2008-09-30
Bump

Please, any comments from anyone using S-Video with a Intel video chip would be appreciated.

---

### Post by C.S.Cameron on 2008-10-21
Bump

---

### Post by SR_ELPIRATA on 2008-10-29
Hey Cameron:

> My wifes D945GCLF works great for her computer needs. 

What ubuntu flavor is it running? Im interested on using it as an option for a simple/basic system, and was thinking on using ubuntu 8.04 with it, but Im not sure yet, could you give me any specifics?

> dual-core Atom and S-video.

I'm going to check this option as well, but Im unsure why would u want S-Video working. Image quality is worse than VGA. I've tested this myself using my nvidia fx5200 and my sony projector and s-video is blurry (because its resolution is lower than even 480p I guess), but when I use the normal vga output the image is sharp. Now Im using the DVI to HDMI so I have a normal LCD and the projector and dont have to keep the projector on all the time.

ELP

---

### Post by mikeofaustin on 2008-12-01
I registered just to reply to this thread.   

   The s-video port does NOT work with this board. I bought the board because the Intel web site said it works with native drivers.   They apparently did not test the s-video port.  VGA works fine, however. 

    If you want to use it for any kind of media center (to place next to your TV), you're out of luck. 

   If you google, you'll find multiple people have this problem with this board. I've even contacted Intel and mentioned that their own site says it's compatible. They ignored me. No love for Intel right now. 

     I'm currently looking for the VIA EPIA boards (VIA based), that support the UNI-CHROME functionality (video decode is handled with video hardware, not the processor). 

-Mike

---

### Post by JRV on 2008-12-14
> **C.S.Cameron said:**
> I'm thinking of building another mini ITX system.
Intel has just released the D945GCLF2 mITX motherboard with  dual-core Atom and S-video.
My wifes D945GCLF works great for her computer needs. 
My daughters D201GLY2 mITX with SIS chipset sucks.
I understand there are issues with S-video and Intel graphics.
The board has GMA 950.
I'm wondering if anybody has gotten S-video working with this board or with GMA 950 in general.

I have been trying to get it working by editing the xorg.conf file.
For my latest attempt I managed to get it working in Puppy Linux 4.11
using the xvesa drivers.
I then copied the monitor section from the Puppy xorg.conf file into the Ubuntu xorg.conf.  It didn't work.
Is there a way to install the xvesa drivers into Ubuntu?
They do not appear to be in the repositories.

---

### Post by jdusablon on 2008-12-16
VESA drivers will work fine for S-video out until you need to use overlay, like when you fire up VLC or mplayer. Then the video mode changes and the sync goes out the window.

This is a xorg issue, not a hardware issue... Windows handles the TV-out just fine.

---

