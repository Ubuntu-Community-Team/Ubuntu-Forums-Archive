---
title: "Kernel panic after B43 driver install on Lenovo IdeaPad S10"
date: 2010-02-14
forum: Hardware
---

### Post by maddog39 on 2010-02-14
Hey everyone,

I just installed Kubuntu 9.10 on my netbook (Lenovo IdeaPad S10). I quickly realized after installing all the updates via a LAN cable that the wireless drivers were causing the system to go into a kernel panic during installation. I first installed the Broadcom 43xx drivers and then the STA drivers and the system kernel panics during the end of the installation process for the BCM STA drivers. After subsequently rebooting the system after the kernel panic, the Hardware Drivers dialog indicates that the drivers were installed correctly and the BCM 43xx driver option has been removed from the menu. I don't really know where to go from here as to resolving this issue so any help would be greatly appreciated.

Thanks in advance!
Alec

---

### Post by efflandt on 2010-02-14
Which BCM device do you have (from output of **lspci**).  I think B43 and STA are mutually exclusive (since activating one deactivates the other), so you should only have one or the other (the proper one for your device).

---

### Post by wojox on 2010-02-14
Install:

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by maddog39 on 2010-02-14
> **efflandt said:**
> Which BCM device do you have (from output of **lspci**).  I think B43 and STA are mutually exclusive (since activating one deactivates the other), so you should only have one or the other (the proper one for your device).
News to me actually, but heres an excerpt of my lspci output :
```
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

> **wojox said:**
> Install:

```
sudo apt-get install bcmwl-kernel-source
```
Did a reinstall of that package, wireless networking still not functional.

---

### Post by andreadelpilarvarlon on 2011-04-03
Hi everyone. I joined here because i was looking for an answer to this problem. I was desperated without wifi. But this might sound stupid.. after my kernel crashed all day everytime i tried to install the STA driver... I just decided to shut down manually the wifi and all the internet connections. So i tried to installed it again and the kernel once again crashed... so i needed to reboot my pc... When i turn on the pc again i had internet connection...


My hypothesis is that the when the computer is installing the driver, the wifi connection needs to be manually shut down (in lenovo computers there is always a button to do it manually) in order to know create interference with the driver installation and the kernel. 

I hope it works on you.

---

