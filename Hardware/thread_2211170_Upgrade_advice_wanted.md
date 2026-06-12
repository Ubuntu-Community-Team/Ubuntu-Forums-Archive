---
title: "Upgrade advice wanted"
date: 2014-03-14
forum: Hardware
---

### Post by jason13 on 2014-03-14
I built my desktop 5 1/2 years ago when I made the switch to Ubuntu. It's served me well as well as gone through incremental upgrades (case, PSU, HDD, graphics card). It's been the trend for me to use up all my memory, to the point where Chrome just grinds to a halt. I have a 3.0 ghz core 2 duo and 2 GB DDR2 RAM, those are the last pieces of my original build other than the sound card and wi-fi adapter. I could upgrade just my RAM to 4 GB (I'm running a 64 bit OS, does DDR2 support more than 4 GB?) for under $70. Or is it getting time to upgrade the CPU and MoBo as well? I don't need a lot of computational power, I have a relatively recent laptop with plenty power for my current needs. If I were to upgrade the CPU and MoBo would my current installation work on the new hardware or would a new installation be needed?

---

### Post by mörgæs on 2014-03-14
If you are unhappy with the speed I would suggest trying X/Lubuntu 13.10 in stead of buying more hardware. 

It's very likely that the installed system will just carry on running on the new motherboard.

---

### Post by grahammechanical on 2014-03-14
> [COLOR=#000000]would my current installation work on the new hardware or would a new installation be needed?[/COLOR]

And what is your current installation? Re-install with Ubuntu 12.04.1 or 14.04 and get a Linux kernel that has been developed for the latest hardware. And also avoid any problems with modules installed for the devices on one motherboard that are not suitable for the devices on the newer motherboard.

As you have noticed, it is not always the OS that runs out of system resources but the applications and how we use them. If I have two large Libreoffice documents running and I set Libreoffice to save both documents then Libreoffice greys out but there is still a lot of System RAM available. And I only have 1GB with my 2.40GHZ Core 2 Duo. I also find that Chromium is a heavy user of RAM.

This statement seems to contradict your reason for upgrading the CPU and motherboard.

> [COLOR=#000000] I don't need a lot of computational power,[/COLOR]

If you have the money and spending it makes you feel good, then you need no excuse to spend.

Regards.

---

### Post by jason13 on 2014-03-14
What I mean is, would upgrading RAM at this point be kind of pointless because my motherboard is quite old and it is likely that it will be the next thing to fail? Or is there a software solution for managing memory I might not have considered?

---

### Post by mörgæs on 2014-03-15
I already pointed to a software solution you could try.

---

### Post by Yellow Pasque on 2014-03-15
> **jason13 said:**
> What I mean is, would upgrading RAM at this point be kind of pointless because my motherboard is quite old and it is likely that it will be the next thing to fail?
Upgrading the RAM sounds like a cheap way to make the system faster if that's what's bottle-necking you. Mobos generally don't fail like hard disks.

> Or is it getting time to upgrade the CPU and MoBo as well?
A 3GHz Core 2 Duo is still a pretty powerful CPU. Unless you're doing something that would really benefit from a faster CPU (like playing demanding games or doing a lot of video encoding), you can probably get more life out of it.

> I'm running a 64 bit OS, does DDR2 support more than 4 GB?
What's going to limit your maximum memory is the mobo/chipset. For example, the Intel NM10 chipset (commonly used with Atom CPU's) won't take more than 4GB (2 in each slot). If you have a Socket 775 board and a Core 2 Duo, I'm guessing your mobo will support at least 8GB, but you need to check the mobo's support site for the offical specification.

> Or is there a software solution for managing memory I might not have considered?
Linux manages memory and it does so very well. Chrome is probably a good part of the issue. I see a lot of complaints that it's a memory hog...
Do you have a swap partition? When your system starts to slow down, look at output of:
```
free -m
```

As mörgæs points out, you can also run lighter desktops to lower RAM consumption. The 'htop' command is your friend to see what's using the memory (you can sort the list by memory usage).

---

