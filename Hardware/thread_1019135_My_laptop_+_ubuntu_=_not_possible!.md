---
title: "My laptop + ubuntu = not possible?!"
date: 2008-12-22
forum: Hardware
---

### Post by Silentzor on 2008-12-22
Hey, i have installed ubuntu, though i had some trouble doing it and i had to do it on low graphics mode, and now every time i try to log on ubuntu i get a black screen. I can't run a terminal or anything, just a black screen. I can enter on the recovery mode only, in order to see any graphics. Any suggestions?

My laptop's config:
Turbo-X
Intel(R) Core(TM)2 Duo CPU T9400 @ 2.53 GHz (2CPUs)
4GB of RAM DDR2
BIOS Revision 1.00.08
NVidia GeForce 9300M GS
Realtek Motherboard Sound Card
I have pre-instaled Windows Vista Home Premium 32Bit

---

### Post by 2hot6ft2 on 2008-12-22
Well if you can get graphics in the recovery mode then you just need to install the graphics driver. System>Administration>Hardware Drivers and be online so it can download the driver and install it. Once it finishes it will require a reboot and should work fine.

---

### Post by Silentzor on 2008-12-24
Not working. Plus i already tried that a bnch of times before

---

### Post by Silentzor on 2008-12-24
Any more suggestions? Now that i did what you suggested it wont even enter on recovery mode ;/

---

### Post by 2hot6ft2 on 2008-12-24
Have you tried to Ctrl+Alt+F1 or Alt+F7 might be Alt+F8 or F9 on yours? It might get you at least to a terminal.

---

### Post by 2hot6ft2 on 2008-12-24
If you didn't have anything important on it you may just be looking at reinstalling it. Since if it was a fresh install somethings not right and it might be the fastest way to go.

---

### Post by Bucky Ball on 2008-12-24
What kernel are you using? If you are using one of the rt (real time) kernels for low latency, they have major issues with the nvidia drivers.

If you can get to recovery, fix all broken packages and also try fixing Xserver. These options are all there when you run recovery (if you can). I had a similar problem and it was telling me 'No Screen' awhile ago, but recovery worked fine.

---

### Post by Stoupeace on 2009-03-30
Hi!
My laptop is almost the same as said above. Only my video card is a SiS model. 

Anyway, i've burned the Ubuntu 8.10 livecd, and tried several times to install Ubuntu. Few things you should know:

1)Booting from the livecd gives a menu with 5 choices.
2)Selecting "Install Ubuntu" or "Try Ubuntu without chaning my computer" leads to a black screen and the laptop seems to freeze.
3)Pressing F6, i had some choices altered and finally got it working. I installed Ubuntu (now i have a dual boot with Windows XP and Ubuntu), and then rebooted. 

When i try to boot from Ubuntu generic (..something..) kernel it freezes. When i try to boot @ the recovery mode, same.

I've installed and unistalled Ubuntu 8.10 several times and the problem persists. 
So it seems to be a hardware problem (i guess...).

Note: Pressing F6 at the boot menu of Ubuntu 8.10 livecd i have to alter all the settings except from the last one, to get it working, so that i can go on and install Ubuntu. You think i did something wrong there..?

Thanx in advance!

---

### Post by Bucky Ball on 2009-03-31
Stoupeace, you might get more mileage from starting a new thread as this is quite old and buried. A good sign your hardware might not be compatible is if the Live version doesn't work. Rule of thumb, if in doubt about compatibility, try the live first. Your card could be the problem. 

I would post a new thread with as much detail as you can muster (machine model/specs) and a descriptive title. Good luck. :)

---

