---
title: "Dual Monitor / External Projector Setup: Problem with Desktop Resolution"
date: 2011-10-18
forum: Hardware
---

### Post by Master One on 2011-10-18
I just did a fresh installation of Oneiric Ocelot 11.10 on my Acer Aspire One 753 laptop, which on its own seems to be working correctly.

The laptop has the odd display resolution of 1366x768, and I want to connect a video projector to its HDMI port, which has the resolution of 1280x720 (HDTV 720p).

Both (the laptop LCD panel and the video projector) are identified correctly, and are automatically configured for the proper resolution.

The problem is now, that the workspace on the video projector seems to be configured at 1366x768, although the display resolution is set to 1280x720, which makes it possible to move the mouse pointer off screen, and which makes it impossible to display a video full screen, since the video player gets maximized to 1366x768 instead of 1280x720.

I already tried all possible settings in the Settings->Display dialog, but I just can not get it right. Somehow when the actual screen display resolution gets changed, the Desktop resolution stays the same as the main display setting (so in my case 1366x768 ).

If I choose the mirror option, I get a terrible low resolution (640x480), because the laptop LCD panel does not seem to offer 1280x720, and the mirror option only works on a common resolution both displays support.

So basically I just want to be able to connect my video projector to my laptop, to watch videos on it. Ideally the laptop LCD display should switch off when the video projector is connected to the HDMI port, and the projector should be choosen as the primary display at the proper resolution (1280x720), but with all my tries I could not get this to work.

Any idea?

So how can I make the video projector to be the primary display at the correct resolution (1280x720) and the Desktop resolution to be be changed from the initial 1366x768 from the laptop LCD panel to the 1280x720 of the projector?

Shouldn't this be done automatically anyway?

---

### Post by Master One on 2011-11-03
I played around with that issue a lot in the meantime, but I could not get it work.

I have now Lubuntu running on that laptop, but it's exactly the same problem.

Even if I reconfigures the screen to 1280x720 with the -fb option of xrandr, and the projector on the HDMI port reports the proper resolution of 1280x720, the screen area on the projector stays larger than the effectively displayed area, making it impossible to view videos fullscreen (and the mouse pointer can still leave the picture in all directions).

The intention is pretty simple, and every desktop setup should be able to handle it without hassle:

Once an external screen is connected (in this case with the HDMI connector on a laptop), it should be possible, to use the external screen with it's real resolution without overhead, so to watch movies fullscreen on the external screen with all picture content shown, and to switch between the internal (laptop LCD) and external (projector) screen, so that I can switch the laptop LCD off, and use the projector as primary screen.

How can this be accomplished?

---

### Post by gwm on 2011-12-06
I have a similar problem. I wanted to watch a movie last night but battled for a long time trying to find how to set it up.

My projector is an old one (800x600) which was automatically recognized. But that's how far I got. How does one get Movie Player, VLC or whatever to use the projector screen?

I couldn't find out how to do it.

---

### Post by Rayaz on 2012-04-17
I too would like a solution to the problem.

---

### Post by henrodon on 2012-05-14
I'm now having a similar issue, but only since I re-installed 12.04. It was working fine before. Now I can't get my external monitor to extend -- it only mirrors regardless of how I set it. Also, I can't set it at any different resolution from the netbook, so any window that's fullscreen on the netbook runs off the edge of the external monitor.

Specs:
Asus EEEPC 1215B
Iiyama ProLite E1906S

---

### Post by roelforg on 2012-05-14
Do you have an ati card?
If so, make sure the propriatary drivers are installed and run this:
```

sudo amdcccle

```
In the display manager menu, you can set the desktops.
The gnome config panel doesn't work well with the ati drivers but the amdcpl works fine.
The links in dash omit the sudo part and run the amdcpl in non-root mode.
I always do this and it works on my acer.

---

### Post by henrodon on 2012-05-15
I thought I replied yesterday, but I don't see my reply here. In any case, I can update what I've tired -- unsuccessfuloly.

I was able to install the ATI driver via Dash and Ubuntu Software Center, though not the driver updates, for no obvious reason. But when I go to the Displays I can't do ANYTHING. Everything I try to do gets the error message "The selected configuration for displays could not be applied."

Any idea what I can try next?

---

