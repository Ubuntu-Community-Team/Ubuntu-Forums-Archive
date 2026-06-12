---
title: "How to get NVIDIA driver"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by swappo1 on 2009-06-14
Hello,

How would I get and install the driver for GeForce 9100 on 8.04?  If I go to administration and click on Hardware Drivers it is not coming up with any and it is not doing a search for hardware drivers.

---

### Post by swappo1 on 2009-06-14
I tried searching for ubuntu-restricted-extras in synaptic package manager.  I insalled all that came up and still now NVIDIA driver is found by my system.  Next I tried manually installing the driver from NVIDIA's site. I shut down the X server and tried to install the driver from the CLI. It said I could not install the driver because I did not have libc development package installed.  What is the libc development package and where can I get it?  I really need help on this.  I have tried everything and am getting nowhere.  All I want is to get my screen set the the right resolution(1920x1080).

---

### Post by mikewhatever on 2009-06-14
Any particular reason to use 8.04? The newest nvidia driver available in its repositories is [169.12]("http://packages.ubuntu.com/hardy/nvidia-glx-new"), and I doubt it has support for your card. Any chance you can use 9.04 instead?

---

### Post by swappo1 on 2009-06-14
I did install the driver on 9.04 and I got the screen resolution to work but my computer was crashing/freezing everytime I opened firefox or a terminal.  I couldn't find out how to fix the problem and my computer was totally unsuable.  I was hoping I could get it to work on 8.04.

---

### Post by TheBuzzSaw on 2009-06-14
The Nvidia provide nForce drivers for Linux?

---

### Post by mikewhatever on 2009-06-14
> **swappo1 said:**
> I did install the driver on 9.04 and I got the screen resolution to work but my computer was crashing/freezing everytime I opened firefox or a terminal.  I couldn't find out how to fix the problem and my computer was totally unsuable.  I was hoping I could get it to work on 8.04.

Assuming the thread related to the installation of 9.04 is [this one]("http://ubuntuforums.org/showthread.php?t=1186946"), I have to ask, 'Did you have the crashes before manually editing xorg.conf?'

---

### Post by swappo1 on 2009-06-14
No, I didn't have any crashing before the installation of the driver.  In fact, if I change the settings of the NVIDIA X Server Settings back to 1600x1200 and click apply, the settings change back.  Then I edit /etc/X11/xorg.conf to reflect the resolution of 1600x1200, save and reboot and the crashing stops.

---

