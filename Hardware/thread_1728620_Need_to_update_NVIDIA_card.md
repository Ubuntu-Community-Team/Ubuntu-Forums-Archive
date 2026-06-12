---
title: "Need to update NVIDIA card"
date: 2011-04-13
forum: Hardware
---

### Post by biohazard135 on 2011-04-13
Hey, I have gone to System > Administration > Additional Drivers and updated my NVIDIA driver, yet this issue still exists. I found a game called "0 A.D." and installed it, however I don't have the correct driver version. It crashes this message:

"You are using 260.19.* series NVIDIA drivers, which may crash the game. Please upgrade to 260.19.21 or later."

Any ideas? Here is my hardware / software:

Ubuntu 10.10 x64
NVIDIA 8400GS 256MB DDR2

---

### Post by Yellow Pasque on 2011-04-14
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by lobelia on 2011-04-18
This was great timing.

I had been having the same problem and couldn't figure out how to close the X server to update my Nvidia driver. Temüjin's solution has been the only one to work for me.

After grabbing the PPA files, I found instructions on this site to install the new drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) .

I used Synaptic Package Manager and updated the two applicable Nvidia drivers and FINALLY the game works great!

---

