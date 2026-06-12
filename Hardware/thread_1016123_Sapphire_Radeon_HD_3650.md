---
title: "Sapphire Radeon HD 3650"
date: 2008-12-19
forum: Hardware
---

### Post by Soldierbane on 2008-12-19
I just got a Sapphire Radeon HD 3650 video card today and installed it my computer. I was really excited when it began to run and said that it had a driver that I needed to install. I proceeded to install the proprietary driver that Ubuntu suggested, and then restart my computer. It appeared to be working up to the point where Ubuntu finishes loading and then I suddenly lose all visuals on my monitor. Any suggestions on what I could to fix this are greatly appreciated. I am very new to linux and I'm not very good at using it yet. The OS is Ubuntu 8.10 and is 32-bit.

---

### Post by Soldierbane on 2008-12-19
OK I just did a full system Reinstall and now it appears to be working. It still wants me to install the proprietary driver ATI/AMD proprietary FGLRX graphics driver. Should I try to download it again? or is there something Else that I should be doing? It says that some GPUs need this in order to fully use the 3d stuff and the 2d accelerator.

---

### Post by markbuntu on 2008-12-19
I have that same exact card, Sapphire Radeon HD 3650 and have no problems with it. This is how I got it to work.
Install Intrepid
wait for the prompt for updates and get them all( ignore the prompt for the restricted driver)
reboot
go to System/Hardware and enable the restricted driver and let it download and install. Reboot again to let the new kernel modules get loaded and it should work. It did for me.

It is very important to do all the updates before installing the restricted flgrx driver. If you are fully updated you should be able to use System/Hardware now to get the card working. After you get it working you can use the Catalyst Control Center to adjust it.

---

### Post by MrDelish on 2009-03-07
I just got Intrepid Ibex working with the ATI Radeon Sapphire 3650. I followed what markbuntu suggested, but the video didn't stop tearing until I disabled all desktop effects. I tried a bunch of other solutions, including removing flgrx completely and installing the open source drivers, but no luck (I'm on a Dell Vostro 220 minitower, for the record).

I can live without fancy animation and such as long as the video works fine.

---

### Post by markbuntu on 2009-03-07
The latest driver from ati 9.2 fixes the tearing issues if you select Xv in gstreamer and the other players.

---

### Post by Sanya18 on 2009-05-08
Hi, I have a problem with my Sapphire Radeon HD 3650 AGP. Ubuntu only works when I restart my computer from windows. When I start my computer when it has powered off, the Xorg doesn't load. Sorry for my English:)

---

