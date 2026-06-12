---
title: "I need help with my nvidia 540m"
date: 2016-06-05
forum: Hardware
---

### Post by gustavokrm on 2016-06-05
Ok, I know this may have been asked hundreds of times, but I don't know what to do anymore.
I installed the drivers via the "additional drivers" thing, and it installed nvidia-prime package. Now, here is the catch: every time I play a game, the entire computer will freeze.
This problem happened on Windows as well, and I could only solve it by using MSI-Afterburner to underclock the card; that way, I could play it as much as I want, but if I leave the card using it's default clock values, it will crash my entire computer.

I have read that I have to use the coolbits option on xorg.conf. I have tried doing that, but it doesn't seem to work, because nothing changes on nvidia-settings. 
I have no idea what to do next. The only thing left to do is to reinstall Windows so I can use msi-afterburner, but it's not an option right now.

My card is nvidia 540m with the nvidia-352 drivers on Ubuntu 14.04.

---

### Post by Linuxisfast on 2016-06-05
In nvidia xserver settings, try to put power mode to min and then see if this issue persists.

---

