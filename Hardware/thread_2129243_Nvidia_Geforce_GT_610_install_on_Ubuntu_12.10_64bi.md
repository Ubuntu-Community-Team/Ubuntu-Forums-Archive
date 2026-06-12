---
title: "Nvidia Geforce GT 610 install on Ubuntu 12.10 64bit"
date: 2013-03-25
forum: Hardware
---

### Post by Blacklight650 on 2013-03-25
Hello all, first post so please forgive if I am asking something alarmingly dumb, here goes. I am trying to get the above named Graphics card installed on my setup - it wasn't straight forward when I had Win 7 installed :( I have downloaded what I believe to be the correct driver although the drivers section of the Java rich nvidia web site was fond of telling me that I don't have the latest Java installed (that's another matter!). Anyway, I have downloaded the file: NVIDIA-Linux-x86_64-310.40.run which of course wont run under Terminal sudo sh NVIDIA-Linux-x86_64-310.40.run - it cannot be run in an X-Window (?) so I searched on how to get up a text console and tried again...I watched with baited breath as something was unpacked and something got processed and then the dreaded blue box telling me once again that the package could not be installed in an X-Window.

What sorcery has to be utilised in order to have this graphics card installed etc by Ubuntu 12.10? Big hearty thanks to anyone that can shed any light on this...I am something of a Linux newbie ...four days and counting! :)

---

### Post by papibe on 2013-03-25
Hi Blacklight650. Welcome to the forums ):P

It is much easier to install the driver provided for Ubuntu itself.

First remove the one you installed. Follow [this]("http://askubuntu.com/questions/207484/remove-proprietary-nvidia-drivers") instructions. 

Since you are running 12.10, installing this would be advisable:
```
sudo apt-get install linux-headers-generic 
```

Then take a look a this [tutorial]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") to install the driver.

It may require a reboot after each step.

Let us know how it goes.
Regards.

---

