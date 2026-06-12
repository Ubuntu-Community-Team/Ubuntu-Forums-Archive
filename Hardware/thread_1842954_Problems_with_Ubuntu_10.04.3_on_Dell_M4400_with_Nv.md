---
title: "Problems with Ubuntu 10.04.3 on Dell M4400 with Nvidia driver"
date: 2011-09-12
forum: Hardware
---

### Post by dwschulze on 2011-09-12
I've got the configuration below and it has several serious problems.  I suspect the NVidia graphics driver.

When I configure the NVIDIA X Sever to use the external monitor as a separate X Screen it throws an error.  I can use it in TwinView mode, but it has the following problems.

In TwinView minimizing windows causes them to disappear and I can't get them back.  The don't show up in the bottom or top panels.  If I click on a different workspace the mouse locks up for a while and when it comes back I can't get back to the original workspace.  None of the buttons on the top and bottom panels will work.  The mouse will move but the laptop is effectively locked up and I have to use the power switch to kill and restart.

I need the NVidia driver to use an external monitor, but the NVidia driver looks like the culprit.

Is anyone else using the NVidia driver for the Quadro FX 770 with Ubuntu 10.04.3 64-bit?

Is there another driver I can try that supports an external monitor?

Thanks.

Configuration:
Dell M4400
Ubuntu 10.04.3 64 bit
NVidia card Quadro FX 770 M
Nvidia driver

---

### Post by dwschulze on 2011-09-12
The problem turned out to be that Hardware Drivers installs 32 bit drivers if you use it to find NVidia drivers.  It doesn't show any 64-bit drivers, even though NVidia has them.

The 64-bit NVidia driver fixes these problems.  Here's how to get and install it:

64-bit driver
[http://www.nvidia.com/object/linux-display-amd64-275.28-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.28-driver.html)

Follow the instructions here:
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
(You'll have to jump through several hoops including temporarily disabling the nouveau driver, but you'll eventually get the 64-bit driver installed.)

Once you have the 64-bit drivers installed when you configure an external monitor you may have to reboot once more to get the xconfig updated.

---

### Post by dwschulze on 2011-09-16
The problems got worse.

After finally getting the 64 bit NVidia driver installed, when I restored the nouveau driver and rebooted my laptop I noticed that it was using the open source driver again.  I Couldn't use my external monitor.  I tried to disable the nouveau driver again (put the generated *.conf file back into /etc/modprobe.d/).  That caused the computer to turn itself off while booting.

This is the first time I've ever been completely locked out of a Linux installation.  My laptop wouldn't even boot.  The 64-bit NVidia driver has serious problems under Ubuntu 10.04.  I've moved to Windows 7 64-bit, and things are working well.

Linux has been a complete failure on the desktop, and this episode illustrates why.  It's the drivers.  Specifically the problems associated with third party drivers.  I'm not just talking about my experience either.  Linux desktop market share has fallen to next to nothing.  The Linux community has to get the driver issue solved.

I hope the situation is better in the 32-bit world, but as far as 64-bit is concerned Linux is not ready for desktop use.

---

### Post by realzippy on 2011-09-16
> **dwschulze said:**
> 
Linux has been a complete failure on the desktop, and this episode illustrates why.  
...nah,sorry,it only illustrates that *you* where not able to (re-)install
a driver.
The twinview issue should be solvable.

---

### Post by Lucamaxx on 2011-10-23
I use Ubuntu 32 bit version with my Dell M4400 since 2 years and I never had a problem with video driver.
Do not know if with 64 bit version things are different, it is clear that if you had install Nvidia 32 bit drivers the you got a problem.

---

