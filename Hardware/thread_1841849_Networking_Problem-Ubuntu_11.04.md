---
title: "Networking Problem-Ubuntu 11.04"
date: 2011-09-10
forum: Hardware
---

### Post by nubtub on 2011-09-10
Hi,

I have a lenovo s10-1, and here are the main specs.
Processor-Intel Atom N270 1.6gHZ
Ram: 2*512mb Sticks
Network Card: Broadcom wireless bcm4312 802.11g wireless
Main OS: Windows Xp,with Natty Narwhal as secondary os in dual boot.

I recently installed ubuntu 11.04 on my windows computer using the wubi.exe file. I dual booted it, but I don't have any network connectivity (it says that the firmware is missing. It works in windows xp.:confused::confused:

Please help, and thank you if you help me.

---

### Post by bcbc on 2011-09-10
Refer to this [http://askubuntu.com/questions/11993/how-do-i-install-bcm4312-wireless-drivers](http://askubuntu.com/questions/11993/how-do-i-install-bcm4312-wireless-drivers)
or this [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

Edit... by the way, since you installed with wubi.exe and you aren't able to connect to the net, you may need to create an ubuntu cd or usb. Wubi actually does store a hidden copy of the ISO when it installs so if you need to you can use this (from a terminal Ctrl+Alt+T):
```
sudo mount -o loop /host/ubuntu/install/.fuse_hidden0000000400000001 /mnt
```

Then you can find packages under:
/mnt/pool/...

---

