---
title: "Freezing desktop GUI on Asus FX505 Tuf Gaming laptop"
date: 2020-10-20
forum: Hardware
---

### Post by david-daking on 2020-10-20
I bought an Asus FX505 Tuf Gaming laptop, with Intel Core i5 CPU and Nvidia GPU.

It came with Windows 10. I booted from USB to live Ubuntu Studio 20.04 and installed it after repartitioning.

I can boot into Ubuntu Studio, but after a few minutes, everything except the mouse freezes. I can move the mouse around, but not click on anything, not drag anything. Key presses do nothing. I can press CTRL ALT F1 for a terminal and do things there. I updated the kernel to 5.8.0-23-lowlatency, but no change.

I would really like to get Ubuntu Studio working on this laptop, as Windows 10 sucks. I can revert it all back to just Windows 10 if necessary, but would rather use Linux.

Any ideas on what is wrong?

Some websites suggest the graphics driver. I have the Nvidia proprietary driver installed and selected, originally the Xorg-nouveau driver was in use, but I removed this as some say it is buggy.

---

### Post by CelticWarrior on 2020-10-20
Which Nvidia graphics do you have and which driver version have you installed and how?

---

### Post by david-daking on 2020-10-20
The graphics: Nvidia GeForce GTX 1650 4GB graphics             
Driver installed via Software & Updates
Version: nvidia-driver-450

---

### Post by david-daking on 2020-10-20
BTW, the laptop also has Intel graphics, how could I switch to using that instead of Nvidia to see if that works?

---

### Post by CelticWarrior on 2020-10-20
Use the Nvidia X Server Settings. Select profile.
[COLOR=#000000]GeForce GTX 1650 is supported by the 430.xx driver, not newer.[/COLOR]

---

### Post by david-daking on 2020-10-21
How do I change the Nvidia driver from the CLI, given that the GUI freezes before I can change it?

---

### Post by david-daking on 2020-10-21
Also, I don't see 430 driver listed, but there is 435 or 418.

---

### Post by david-daking on 2020-10-21
Update: the 418 driver is a server driver, so i went with 435. It worked okay for a while, I even installed and opened the Gnome System Monitor, and it is running now, and showing real time updates on CPU usage etc., but the whole thing is still frozen as in cannot click on anything, and cannot do things like Alt-Tab. CTRL ALT F1 works for a terminal screen.

---

### Post by CelticWarrior on 2020-10-21
The [Graphics Drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") provides among others the 430 driver you currently need, according to Nvidia.

Add the PPA and then you'll be able to select and apply the proper version in Additional Drivers. Using this GUI tool should remove all the other versions installed before installing your selection but if not use ```
sudo apt-get remove nvidia*
``` to start from a clean slate.

---

### Post by david-daking on 2020-10-26
I did as you suggested, and added that Graphics Drivers PPA, but I am back to where I was. There is no Nvidia 430 driver listed, and it freezes still after a while. Using the later kernels makes it even worse. I am ready to give up on this as it's not working with no obvious solution.

---

### Post by david-daking on 2020-10-26
I am going to try Kubuntu, as someone else somewhere else suggested that Kubuntu worked for them.

---

### Post by david-daking on 2020-10-26
I did some updates and installed nvidia-driver-455 (open source) but after rebooting I still have the same problem.

---

### Post by CelticWarrior on 2020-10-26
[COLOR=#000000][INDENT][B][I][COLOR=#000000]GeForce GTX 1650 is supported by the 430.xx driver, not newer.
[/COLOR][/I][/B][COLOR=#000000]Check with Nvidia if you don't believe.

There is 430 in the Graphics Drivers PPA, go the page and check for yourself. If you don't see it you did something wrong.[/COLOR][/INDENT]


[/COLOR]

---

### Post by david-daking on 2020-10-27
Which PPA do I add?

---

### Post by david-daking on 2020-10-27
I installed Kubuntu 20.04 to the same laptop, in a different partition, and although there were problems with installation, it still booted and is using the nouveau driver, so far without freezing. However, I still do not have audio in either Ubuntu Studio or Kubuntu. And the nouveau driver still caused freezing in Ubuntu Studio.

---

### Post by david-daking on 2020-10-27
Update: Kubuntu 20.04 working with nouveau graphics driver and got sound working. However, when I closed the lid of the laptop, and later reopened, the laptop is still on because the keys are lit up, but the screen is completely blank. No key presses do anything, cannot get it back to anything displaying on the screen. Just prior to that, I had installed the xscreensaver, but not set it up at all.

---

### Post by Yellow Pasque on 2020-10-28
If you punch in the details on Nvidia's site, it will bring up 435.21, where the GPU is listed as supported: [https://www.nvidia.com/Download/driverResults.aspx/150803/en-us](https://www.nvidia.com/Download/driverResults.aspx/150803/en-us)
It is very strange to me that they specifically cut out the mobile 1650 from newer versions, but there are still a bunch of older GPU generations supported as well as the mobile 1650Ti. It may be an error (wouldn't be the first time).

As for changing to Intel in CLI (when using Nvidia proprietary driver):
```
sudo prime-select intel
```

---

