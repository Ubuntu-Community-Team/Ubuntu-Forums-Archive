---
title: "Presario CQ60-300EO"
date: 2010-05-23
forum: Hardware
---

### Post by Ecaz on 2010-05-23
Hi, I just installed Ubuntu 10.04 64bit version on my HP Compaq Presario CQ60-300EO.

But in the Network options attached to the top panel the "Enable Wireless" is grayed out and is therefor impossible to be clicked.

I don't know if I have Broadcom, Artheros or something different but in Synaptic Package Manager it says bcmwl-kernel-source and it's installed and the checkbox is green but when I go to Hardware Drivers I don't see any Broadcom I only see NVidia Stuff.

Also there is a button to enable/disable the wireless card in the laptop but when I press the button to disable it (The card is always active) still stays active.

So is the driver installed wrong?
I went on Broadcom site and downloaded the driver and in Terminal I typed MAKE
Then I removed it and installed from the package in which it comes with Ubuntu 10.04

There was an update for Ubuntu or at least it tells me in the update manager to download some stuff, I did but no success.

How can I fix the problem with it being grayed out?

---

### Post by ajgreeny on 2010-05-23
Show us the output of ```
lspci
``` and ```
sudo lshw -C network
```to show your wireless adapter make and chipset and it may be easier to tell you where to get the driver.

---

### Post by ed-rapley on 2010-05-25
Take a look at this thread, with posts 3 and four, i got my fujitsu amilo wifi working.

[http://ubuntuforums.org/showthread.php?p=9354354#post9354354](http://ubuntuforums.org/showthread.php?p=9354354#post9354354)

good luck.

---

