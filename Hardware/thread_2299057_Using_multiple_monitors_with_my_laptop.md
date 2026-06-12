---
title: "Using multiple monitors with my laptop"
date: 2015-10-15
forum: Hardware
---

### Post by Terrance_Tibbs on 2015-10-15
Hello guys,
  I have a HP Pavillion g6 Notebook with a AMD A8-4500M processor with 1 external monitors. 
I'm currently running ubuntu 14.04 LTS. I heard that it was possible to have 2 (external) monitors
 but I couldn't find any reliable information on how to do this on a linux based machine. A friend suggested
 that I buy a USB to DVI HDMI VGA Multi Display Adapter. I only seem to find Adapters
that are compatible with Windows and Mac.

 Is ubuntu 14.04 linux compatible with these Adapters? If so, which ones work with ubuntu 14.04?

---

### Post by Lars Noodén on 2015-10-15
Once the video gets to the video port, it is independent of the OS.  From a little searching of reviews, it looks like the HP Pavillion g6 Notebook has both a VGA port and an HDMI port.  So choose the adapter between HDMI or VGA to whatever your monitor uses.

---

### Post by Terrance_Tibbs on 2015-10-15
My laptop does indeed have a HDMI and VGA port but once I connect them up to my laptop (with 2 separate cables), my laptop
screen goes blank and my images are displayed on the 2 external monitors.
 This is the reason I am looking at alternatives.Does anyone have an idea how to resolve this issue?

Let me try to put this question another way.
NOTE: Please do not answer unless you know or you have done it, thank you.

Has anyone managed to connect up 2 or more monitors to their laptop that 
is running ubuntu 14.04? If so, which specific USB graphics Adapter did you
use? i'.e, name of manufacturer etc.
 Thank you.

---

### Post by Lars Noodén on 2015-10-15
> **Terrance_Tibbs said:**
> Has anyone managed to connect up 2 or more monitors to their laptop that 
is running ubuntu 14.04? 

On a [System76 GazellePro](https://system76.com/laptops/gazelle#specs) using its Intel HD 4600 graphics, I can have one independent display on HDMI, another on VGA and a third on the built-in screen.  So, to answer the question whether it is in general possible to have two external monitors on a laptop running Ubuntu 14.04, the answer is yes.

---

### Post by Terrance_Tibbs on 2015-10-15
Great, now do you use 2 standard cables: one being a VGA cable and the other being a HDMI cable? or do you use a graphics adapter of some sort?
Thank you.

---

### Post by Lars Noodén on 2015-10-15
> **Terrance_Tibbs said:**
> Great, now do you use 2 standard cables: one being a VGA cable and the other being a HDMI cable? or do you use a graphics adapter of some sort?
Thank you.

I use just standard cables, one VGA and one HDMI.  It works out of the box, automatically detecting the attached monitor(s).  I mainly use just the built-in screen, and just occasionally an external monitor.  Very rarely I use two external monitors.  No graphics adapter is needed with the hardware I have for any of the arrangements.  According to lshw, the HD 4600 uses the i915 drivers, which the system supplied automatically with no intervention on my part.

---

### Post by Terrance_Tibbs on 2015-10-15
Brilliant thank you !! :D

---

