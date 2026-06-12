---
title: "Video Memory Corruption - Kernel or HW problem?"
date: 2011-02-17
forum: Hardware
---

### Post by casperlingus on 2011-02-17
OS:     Ubuntu 10.04 64-bit
CPU:    AMD Athlon II X3 440
GPU:    NVIDIA GTX 460
Driver: NVIDIA Manual Install 260.19.36 (also happened w/ 260.19.29)

Built my computer about 8 months ago, and had no problems.  For graphics stress, I play Minecraft occasionally, and do CUDA programming on this machine for work (nothing too stressful, though).  I track my GPU temperature via the GNOME Sensors widget on my top panel.  I've never seen it get above 56 deg C.

Just recently, I started getting video corruption on my desktop.  Within an 10 minutes of booting and using my computer, I get a chunk of my desktop corrupted.  It's always exactly one block 800x300 (approx) of my desktop, different location every time.  It is showing some other part of video memory, whenever that color should be white/background.

-- If the color should be white (or maybe background color for gnome theme), it shows this other memory
-- If the color is not white, it displays normally.  If it's a mixture, only the white pixels are replaced.
-- It does **not** show up in a screenshot
-- [Click Here]("http://dl.dropbox.com/u/1139081/videocorrupt.png") to see a picture of it from a digital camera
-- It seems to be linked to the video memory used for games.  As I play Minecraft, it actively displays a distorted chunk of the game.  After I close the game, it just keeps that same chunk there indefinitely.
++ When I'm in Windows this does **not** happen.
++ Video Mem Test using DirectX and CUDA in Windows ran for 8 hours, and found no errors

I wanted to try a bootable Video Mem test, but VMT-boot won't load properly.  I can't seem to find any other programs that will do a bootable GPU memtest.

Given the evidence above:
     (1) Could this be a kernel problem?  (only happens in Linux)
     (2) Is this more indicative of HW or SW problem?
     (3) Are there any programs I can use that will test/stress the lower-level video memory operations?  Windows or linux would do fine.  I'm surprised at how difficult it is to find such a program.  

-Casper

---

