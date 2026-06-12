---
title: "problem,nvidia drivers"
date: 2010-07-30
forum: Hardware
---

### Post by harpinder on 2010-07-30
hi everyone
i have installed ubuntu 10.04 on my acer aspire 4520 successfully.after that i installed nvidia drivers version 173 and current.at that time they were working.after that i updated my system.now these drivers are not working for me.i reinstalled these driver but same problem.
in the hardware drivers menu these are listed.now i have activated the version 173 at the menu message is showing that this driver is activated and in use but i am not getting any effects which i previously get.
so please help me in getting these effects.
i am a newbie.thanks.

---

### Post by Cincinnatux on 2010-07-30
This is a known issue.  See:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA driver activated but not currently in use in ubuntu 10.04]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA driver activated but not currently in use in ubuntu 10.04")

I am having a similar problem.  I'm running nVidia's 256.35 driver for my GeForce 8400M GS card on a Dell XPS M1330 laptop, all under 32-bit Lucid Lynx.  Fresh install as of this morning.  As with the bug identified above, System=>Administration=>Hardware_Drivers shows that nVidia-current is 'active but not in use.'  

As far as I can tell, however, it *is* in use.  I have Compiz 3D effects working, etc.  So go to the link I provided above and give it a try.  It may not change whether the system reports the driver as being in use, but it will hopefully restore full graphics capabilities to your machine.

---

### Post by harpinder on 2010-07-31
i gave a fresh install and download nvidia drivers.now its working.
anyway thanks.

---

