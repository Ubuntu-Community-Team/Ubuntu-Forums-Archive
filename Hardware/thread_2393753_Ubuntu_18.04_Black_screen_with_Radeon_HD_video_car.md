---
title: "Ubuntu 18.04 Black screen with Radeon HD video card"
date: 2018-06-07
forum: Hardware
---

### Post by leunam12 on 2018-06-07
Hi, I just installed Ubuntu 18.04 on my HP DV6 laptop. It was working well but all of a sudden it started booting to a black screen.
At that point the only thing that I can do is blindly open the terminal with CTRL+ALT+T and reboot.

my video card is ```
Advanced Micro Devices, Inc. AMD/ATI Whistler Radeon HD 6630M/6650M/6750M/7670M/7690M
```
adding nomodeset to GRUB fixes the problem but it creates other problems such as graphics too slow and things not appearing on the screen.

Thanks

Update: Closing the lid, opening and clicking on the touchpad button will give a working screen

---

