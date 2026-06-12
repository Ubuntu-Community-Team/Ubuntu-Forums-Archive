---
title: "Karmic and HP Envy 15"
date: 2009-12-15
forum: Hardware
---

### Post by bluegreen7hi on 2009-12-15
Alright so I just got my brand new HP Envy 15 in the mail yesterday. Opened it up, checked to make sure the BIOS was up to date (it was, F.06), and installed Ubuntu 9.10. The entire installation goes fine and it reboots. This is where my problems start. First, it will show the white Ubuntu logo in the center of the screen, then the screen just goes black. It seems X is having trouble starting. Sometimes however, with numerous reboots, I can actually reach a desktop. I enable the ATI driver, and reboot. Now with the driver enabled, Ubuntu will ONLY boot in low graphics mode. Is anyone else having these 2 problems with the Envy 15?

---

### Post by jdos2 on 2009-12-18
It sounds like you updated to the close-sourced driver at some point in time. The closed source driver will NOT work with the latest version of X on Ubuntu (the one distributed with 9.10, for instance)- the update kills the machine, and I've not yet figured out how to back it out.

So... Just run the open source version of the driver- it works well enough for video- just no 3D acceleration.

Curious how you solved the Touchpad issues or are you just using a mouse? Have you had trouble burning CD's? Decent battery life? Did you get sound working?

I got much of it solved- PM me (or search the forums) if you've not gotten everything working. I'm good, all the way up to the CD burning.

---

