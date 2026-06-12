---
title: "NVIDIA 346 driver thinks I have multiple monitors"
date: 2014-11-17
forum: Hardware
---

### Post by Aide9aic on 2014-11-17
Anyone else seeing a problem where the driver thinks you have multiple monitors when you actually don't?

My ThinkPad T520 (with Utopic) has a GF119M (Quadro NVS 4200M) chip. I've disabled the Intel graphics in the firmware and use only the NVIDIA. The laptop has a VGA port and a Displayport, neither of which is connected to anything -- I'm using only the built-in 1920x1080 LCD panel.

When I boot with the 346 driver from the Xorg Edgers PPA, the driver thinks that a monitor is attached to the VGA port and creates an X screen 3840 pixels wide (2 x 1920). This, of course, is obviously unusable, since my LCD now displays only half the "screen." Relevant lines from **Xorg.0.log**:
```
(--) NVIDIA(0): Lenovo Group Limited (CRT-0) (connected)
(--) NVIDIA(0): Lenovo Group Limited (DFP-0) (boot, connected)
...

(II) NVIDIA(0): "DFP-0:nvidia-auto-select,CRT-0:nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 3840 x 1080
...

(II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,CRT-0:nvidia-auto-select"
```

I reverted to the 343 driver, which properly detects that nothing's connected to the VGA port:
```
(--) NVIDIA(0): CRT-0
(--) NVIDIA(0): Lenovo Group Limited (DFP-0) (boot, connected)
...

(II) NVIDIA(0): "DFP-0:nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
...

(II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
```

I tried forcing only the metamode for DFP-0 (the LCD panel) but that didn't work. I might have been doing that wrong, though. For now, I'm sticking with 343.

([More detail with screenshots, if you're interested]("https://www.kubuntuforums.net/showthread.php?66869"))

---

