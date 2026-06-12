---
title: "Disable touchpad while typing"
date: 2018-11-28
forum: Hardware
---

### Post by daredevildas on 2018-11-28
My palm occasionally brushes against the touchpad while I am typing, thereby causing unwanted movement of the cursor. 

Palm detect is set to 1. 
pratyush@pratyush-GS65-Stealth-Thin-8RF:~$ synclient | grep Palm
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200

In dconf-editor I have enabled "disable touchpad while typing"

My touchpad is synaptic.
Laptop - MSI GS65
OS - Ubuntu 18.04

---

