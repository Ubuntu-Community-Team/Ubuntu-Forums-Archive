---
title: "Asus P5Q Pro Mobo - No PC Wakeup from Standby"
date: 2010-08-05
forum: Hardware
---

### Post by zamar28 on 2010-08-05
I just installed Ubuntu 10.04 LTS 64-bit, and like it. Unexpected set back though: after being sent to Suspend by clicking the Menu Option, the PC can't wakeup. Neither by moving a MS USB Wireless Mouse or clicking buttons on Wireless Keyboard, no by briefly pressing a Power Button on the PC. Of course, USB Wakeup options are properly jumpered on the Mobo and preselected in BIOS, and they work perfect on the same PC in Windows. But in Ubuntu absolutely nothing happen when trying to wakeup by the peripherals. When pressing Power Button, Hard Drive and fans start spinning, but there is nothing on the Monitor hooked via a DVI port to ATI 3700 series GPU. When I then reboot the PC by Power Button, Ubuntu either hangs and needs reboot (at times successful), or boots after a long struggle (possibly re-mapping all hardware again). 

Why wakeup represents such an ongoing problem for Ubuntu? Why there is no option in Device Manager for each suitable device to be "enabled" or "disabled" to wakeup a PC, similar to Windows? In fact, in Windows there is a separate fix (presented as a separate device) to prevent accidental mouse movement to wakeup the PC, i.e. these issues are carefully worked out. What's wrong with Ubuntu? Any way to fix these issues? My first impression is, there are multiple issues, including the need to manually change config files to select devices for wakeup, and fixing DVI & HDMI related monitor wakeup issues. Any Configuration or Tweak Manager in Ubuntu allowing to choose wakeup devices without modding files manually? Any DVI fix or whatever it may be monitor related (may be Ubuntu graphics support can't read EDID on wakeup)? Again, all hardware works just fine in Windows. And it works OK in Ubuntu, including GPU with generic Ubuntu or ATI drivers, except the wakeup issue.

---

### Post by zamar28 on 2010-08-06
Anyone can suggest a package allowing to set advanced power management options in Ubuntu, possibly including what device can control system wakeup from Suspend?

Also, why there is no Standby option in Ubuntu 10.04 Menu?

---

