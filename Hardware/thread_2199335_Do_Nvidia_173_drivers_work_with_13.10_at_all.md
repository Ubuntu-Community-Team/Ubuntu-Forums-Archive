---
title: "Do Nvidia 173 drivers work with 13.10 at all?"
date: 2014-01-13
forum: Hardware
---

### Post by Doj on 2014-01-13
Hi there.

I've got some really old hardware with an Nvidia FX-5200 graphics card, and have tried everything I can to get a working driver running. I know Nvidia support the card with the legacy 173 driver. I'm using Lubuntu 13.04 32-bit.

When installing the driver using 'sudo apt-get install nvidia-173' the computer will boot to a flashing cursor and I can press Ctrl-Alt-F1 to do things.

When I uninstall the driver it boots to a completely black screen and I can get to a desktop (small resolution, but I'm using it now) by booting in recovery mode and pressing continue. I believe this might be because I blacklisted nouveau in /etc/modprobe.d/blacklist.conf.

If I try to install the Nvidia 173 .run from their website it won't compile because it can't find a version.h in the kernel sources. This leads me to believe that there might be a problem with newer kernels.

Is it even possible to run the drivers properly on these old computers?

I would appreciate any help or advice. I can run Lubuntu using the integrated Intel card only, but it gets tedious when I want to switch between Windows XP and Lubuntu, I have to swap out the card.

Thanks.

---

### Post by Doj on 2014-01-20
Obviously not.

After a bit of research I found that you need to downgrade the version of X to be able to use these drivers. I don't think I'll be doing that.

Thanks for the help.

Jodie

---

### Post by justtryit on 2014-01-20
I found this thread by searching for +nvidia+black+screen.  Thank you.  

Now, after two back-to-back unsuccessful installs  (and, of course,  twice enduring the consequent endless update processes on a slow DSL connection) both ending in black screens after the 'additional drivers' section, I am about to start a third install.  THIS time I plan to just skip those pesky nvidia (173/304/304update?) proprietary drivers, and just see how it goes without them.  (Do I even need those if I don't play any computer games?)

NVIDIA GeForce 6150 LE
UBUNTU 12.04.3 64BIT
Total Beginner (One successful install - just not today)

---

### Post by VMC on 2014-01-20
I have a 6150 SE, I need them, because of freezes using gnome-control-center. I install nvidia-304.116 and everything works fine.

---

### Post by jp734 on 2014-01-21
Hmmm...you got me wondering what driver is being used on my desktop with the same card (nvidia fx5200)...It is working perfectly with dual monitors. All I had to do was ad the device and monitor configuration files under /usr/share/X11/xorg.conf.d folder...I know I installed the open source driver 173...

---

### Post by justtryit on 2014-02-01
Success.  Thank you! 

Further regarding the above problem, I was/am being offered both nVidia 173 and 304, which apparently reference different kernels, causing an API mismatch.  I didn't reinstall Ubuntu this time - fortunately I discovered I could use recovery boot to get a command line, and just remove the 173 and the 304, then reinstall the 304 alone, skipping the 173 package all together, and it appears I am now running okay with Ubuntu 12.04 64bit (with Ubuntu showing RAM as 7.7gb)

(Also obtained, and have begun to work through, a pdf copy of The Linux Command Line, Second Internet Edition, by William E. Shotts, Jr., which hopefully will help begin to lead me out of the darkness.)

HP m7664x w/ nVidia 6150 LE and Athlon64x2 4200+ Windsor Dual-Core with 8gb RAM (4 X  2GB-Corsair CM2X2048-6400C5, DDR2-800)  installed on NODUSM3  motherboard, Ubuntu 12.04.3-desktop-amd64 now dual booting successfully with original 32bit install of winXP-MCE.

---

