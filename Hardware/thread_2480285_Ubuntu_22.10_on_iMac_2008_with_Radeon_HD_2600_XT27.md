---
title: "Ubuntu 22.10 on iMac 2008 with Radeon HD 2600 XT/2700 GPU"
date: 2022-10-24
forum: Hardware
---

### Post by svenole on 2022-10-24
I originally installed 22.04 on my old iMac (scratched it completely) and it worked very well with one exeption. The suspend function did not work. The display went pink and fuzzy, but I could see what was going on so I had the possibility to reboot the system. Then it worked fine again. I experimented with some AMD drivers without success. I was able to install proprietary drivers, but then the display was completely messed up after boot so I had to get back to the default graphics driver and live with suspend not working. 

I then upgraded to 22.10 to see if this would fix the issue. It did not. It made it a bit worse in fact. No the iMac wakes up the same way with a fuzzy display, but this time the suspend hangs and I have to use the Swedish button to reboot. 

I`ve done a lot of search for a solution for this issue without success so far. It seems to be related to the old Radeon graphics hardware. I did see that someone suggested to add the boot option "nomodeset", but this messed up the display after boot the same way as when the proprietary driver was installed. 

Anyway - Ubuntu 22.04 and 22.10 runs flawlessly on this old iMac and I can live without the suspend function. However, feel free to suggest something I can try out to make this work .

---

