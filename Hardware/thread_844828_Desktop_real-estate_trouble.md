---
title: "Desktop real-estate trouble"
date: 2008-06-29
forum: Hardware
---

### Post by mrm0rbid on 2008-06-29
I can't quite seem to get m multi screen set-up working... I've tried enabling desktop effects, and I can't locate screens and graphics like i could in 7.10 (standard version, ubuntu). I don't have onboard, Im using GeForce 6600 with a dvi to VGA and standard VGA ports, along with a no-name graphics card to eaqual 3 displays, yet I can only seem to get 1 screen working...........


Help?

---

### Post by chewearn on 2008-06-30
> **mrm0rbid said:**
> I can't quite seem to get m multi screen set-up working... I've tried enabling desktop effects, and I can't locate screens and graphics like i could in 7.10 (standard version, ubuntu). I don't have onboard, Im using GeForce 6600 with a dvi to VGA and standard VGA ports, along with a no-name graphics card to eaqual 3 displays, yet I can only seem to get 1 screen working...........


Help?

Use nvidia-settings to set-up.  Install it by [click here]("apt://nvidia-settings") or run the command below in a terminal:
```
sudo apt-get install nvidia-settings
```Run the program with root privilege:
```
gksudo nvidia-settings
```Remember to click on "Save to X configuration" after you have set-up the displays.

---

