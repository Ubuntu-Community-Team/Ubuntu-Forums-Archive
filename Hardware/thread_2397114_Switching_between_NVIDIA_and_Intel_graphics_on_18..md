---
title: "Switching between NVIDIA and Intel graphics on 18.04"
date: 2018-07-25
forum: Hardware
---

### Post by rimorob on 2018-07-25
Hello all, 

I'm running Ubuntu 18.04 on a Lenovo T430 laptop with NVIDIA NVS 5200M (discrete) and Intel Graphics 400 (integrated).  I have been able to get Ubuntu to run with NVIDIA, which required downgrading to NVIDIA driver v350, but I can't seem to use prime-select intel to switch into intel mode.  I have found internet evidence that I should use lightdm/Xorg rather than Gdm3/Wayland, and indeed, I was able to prevent blank screen/flicker on login, but I still have a login loop, where lightdm returns me back to the login script after I try to log in.  However, for reasons of power usage, I would really like to figure out how to switch into intel mode.  

Currently, my bios has Optimus enabled, but when I enable integrated graphics I see exactly the same behavior as if I choose "prime-select intel".  Any advice?  I've just sunk two hours into googling this, and there seem to be some active bugs, but none of the proposed work-arounds seemed to work for me.


Thanks in advance!

Boris

---

