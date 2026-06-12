---
title: "Upgraded Video Card to PNY NVS300 - Screen completely blank after POST"
date: 2011-11-01
forum: Hardware
---

### Post by b4sher on 2011-11-01
Hello all,

I have recently upgraded my video card after installing Ubuntu 11.10 (x86) to a PNY NVS300 video card. I have seated it correctly and POST displays perfectly on it. However, when Ubuntu begins to boot, the screen goes completely black (as if nothing was plugged into the display at all). I wait for it to boot up and press ALT+F4 to try to get to a terminal, but the screen refuses to turn on. I need to install the video driver for it, but in order to do so, I have to have the card physically installed on the machine. Whenever I revert back to onboard graphics, Ubuntu runs fine.

I tried changing my /etc/default/grub from "quiet splash" to "single" and ran "update-grub" as root.

Machine specs:

Dell SC1430 - Intel Xeon Quad Core - 8GB RAM

Does anyone have any suggestions. Please advise!

Thank you

---

### Post by 2F4U on 2011-11-01
Did you already try the safe boot option? Else, it may help to use the grub kernel parameter

nomodeset

---

### Post by b4sher on 2011-11-01
I haven't, and when using the card, it won't let me get to the point of choosing my boot method (recovery, memtest, etc...) so the grub menu is never displayed throughout this process. The last thing I see before the screen goes out on me is the information of my RAID controller. When using onboard, I can see the entire startup and load, and then log into X successfully.

I'll try the grub kernel param and report back. Thanks for the reply.

---

### Post by b4sher on 2011-11-02
I was able to fix the problem. I booted from my onboard card and downloaded boot-repair (hxxps://help.ubuntu.com/community/Boot-Repair). I initially used the recommended repair, then went in a did a manual setting to "nomodeset" as previously advised. I booted the computer with the new card and it was still quite unconvincing that it would work properly, but it finally brought me to a login prompt (after a few minutes of flickering). Was able to install the nVidia drivers at that point as well.

Thanks for the help!

---

