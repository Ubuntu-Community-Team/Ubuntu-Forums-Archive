---
title: "Nvidia kernel modules not loaded on startup (but they work when loaded manually)"
date: 2014-01-24
forum: Hardware
---

### Post by andreselsuave on 2014-01-24
Hello, 

I installed the xorg-edgers ppa to get the latest nvidia drivers for my card, but when I did, lightdm didnt manage to start. I uninstalled xorg-edgers ppa with ppa-purge package.

Now I installed nvidia_319_updates and when I boot up the computer lightdm won't start. However, when I go to the terminal and type:

```
modprobe nvidia_319_updates; sudo service lightdm start
```

Lightdm will start and everything will work fine. It looks like ubuntu forgets to load nvidia kernel modules and I have to do it manually everytime I reboot. 

Is there a way to get it back to working automatically?

Thank you very much!

---

### Post by lz_yong on 2014-01-24
> **andreselsuave said:**
> Hello, I installed the xorg-edgers ppa to get the latest nvidia drivers for my card, but when I did, lightdm didnt manage to start. I uninstalled xorg-edgers ppa with ppa-purge package.Now I installed nvidia_319_updates and when I boot up the computer lightdm won't start. However, when I go to the terminal and type:```
modprobe nvidia_319_updates; sudo service lightdm start
```Lightdm will start and everything will work fine. It looks like ubuntu forgets to load nvidia kernel modules and I have to do it manually everytime I reboot. Is there a way to get it back to working automatically?Thank you very much!It seems you need to recreate the initrd file. that is (before doing this you should check if the nouveau has been blacklisted.)$sudo update-initramfs -usee this page "http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html" for more infomation.However I should highly warned you, with nvidia card drivers in the ubuntu, bad things happen out of your expectaion.  Just make sure you know what you are doing, before action.

---

