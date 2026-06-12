---
title: "Sony VGN-SZ240P + VGN-PRSZ1 Docking and external monitor"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by sagyvolkov on 2006-10-16
Hi All,

I'm new to ubuntu and new to the X world, but i've worked many years on Unix systems - just never used a lot X beside xterm.
Anyway, I've got this Sony VGN-SZ240P connected to a sony docking station (suppose to be a docking station) VGN-PRSZ1.
I've been searching to find how to have my Dell 20" LCD that is connected via DVI to the docking station to show any signs of "life" from the laptop while running ubuntu.
For start, how do i even know that the kernel even recognized the external monitor? 
Once i get that figured out, this laptop has two video cards, intel and NVIDIA, i'm using the NVIDIA GeForce Go 7400 video card, from reading here, i've understood that i can either clone the whole screen to the external monitor or actually have the laptop monitor desktop be extended to the external LCD, am I correct? So i do set this up?

Any help and advice will be appriciated

---

### Post by sagyvolkov on 2006-10-23
No can help?
Please....

---

### Post by vishketan on 2008-02-17
I have a sony vaio vgn sz483n which has similar configuration as yours. My laptop has a stamina mode (intel  integrated video card) and a speed mode (nvidia geforce go 7400 video card). First of all note that DVI output is not available when using the Intel card (its disabled in hardware as far as I can tell). 
To get DVI out on the nvidia card install the nvidia proprietary drivers (go the restricted driver manager and install it from there). Then from the terminal run 

sudo nvidia-settings

it should give you a nice GUI for configuring dual monitors. 

But I am getting the same problems as this post

[http://ubuntuforums.org/showthread.php?t=666757]("http://ubuntuforums.org/showthread.php?t=666757")
  
If I undock while running X the whole machine freezes over and the only way I can shut it down is to disconnect the battery!

vishy

---

