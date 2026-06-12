---
title: "Video corruption with ATI Radeon 7000 (RV100) and XBMC 9.04"
date: 2009-05-25
forum: Hardware
---

### Post by bakra01 on 2009-05-25
Hi,

I already posted this same question in the XBMC forum, but without a result. Hope anyone can help me here.

I've been looking trough the XBMC forum and can see others with he same problem, but they are using Catalyst.

My problem is corrupted video like in this picture:
[http://img72.imageshack.us/img72/262...shot005qc8.png]("http://img72.imageshack.us/img72/262...shot005qc8.png")
or this one:
[http://img215.imageshack.us/img215/9...shot001cy2.png]("http://img215.imageshack.us/img215/9...shot001cy2.png")

The UI of XBMC is OK. Also video in background is OK. The problem only occurs when in fullscreen.

I'm using the default radeon driver in Jaunty
Already tried to add the advancedsettings.xml, with no result.

My configuration:
Ubuntu 9.04
ATI Radeon 7000 AGP (RV100)
Default Radeon driver
XBMC 9.04

What do I have to do to solve his?

---

### Post by pnhers on 2009-06-20
Seems like i have the same problems... When you start a video, the screen stays black. When you go back to xbmc the video plays correct in the preview section. When you go back to full-screen mode the video plays correct. But than if you enable the osd, the video behind the osd disappeared. The osd self is also wrong.

I had also problems in Elisa media center, related to this topic. The previews of the images where also wrong. Now Elisa is changed to Moovida, i can't use the program anymore. I think there are bugs in the radeon drivers for the RV100 cards (ati radeon 7000). 


to bakra01: 
You post the wrong links to the pictures. Your link contain "..." i don't think that's correct.

NOTE: i also tried the "glrectanglehack" hack

Here a picture of the scrambled osd
[IMG]http://www.yarf.nl/ubuntu/XBMC_screendump.png[/IMG]

And the scrambled Moovida
[IMG]http://www.yarf.nl/ubuntu/Moovida_screendump.png[/IMG]

---

### Post by bakra01 on 2009-06-28
That is exactly the same picture I had!
I solved that by changing the resolution in XBMC in 1080p 60Hz.
But now I,ve got the problem that the video is far behind on audio.
Probably because the videocard is not fully supported by XBMC.

---

