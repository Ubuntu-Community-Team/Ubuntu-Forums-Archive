---
title: "PCIe Bus Error 1c.5 Ubuntu 20.04 LTS"
date: 2020-08-10
forum: Hardware
---

### Post by wizardoveryonder on 2020-08-10
I've done a fair bit of searching and tried a few fixes, but I am yet to find a solution. 


[LIST]
[*]ASUS K501U Laptop
[*]Intel Core i5 (6th Gen) 6200U / 2.3 GHz Max Turbo Speed 2.8 GHz Processor
[*]8GB RAM
[*]1TB HDD
[*]1920 x 1080 Resolution
[*]NVIDIA GeForce GTX 950M 2GB GDDR3 Graphics (Yes, it is "optimus")
[*]Ubuntu 20.04.1 LTS (Installed 07/08/2020 - Dual Boot with Windows 10)
[/LIST]
I noticed my /var/logs/ folder was **155GB** :O so I watch tail'd it: 

```
watch tail /var/log/syslog
```

I was getting the following error at least once every second:

```

pcieport 0000:00:1c.5: AER: Corrected error received: 0000:00:1c.5
pcieport 0000:00:1c.5: AER: PCIe Bus Error: severity=Corrected, type+physical Layer, (Receiver ID)
pcieport 0000:00:1c.5: AER: device [8086:9d15] error status/mask=00000001/00002000
pcieport 0000:00:1c.5: AER: [ 0] RxErr

```

My NVIDIA driver is up to date, and as far as I can tell is working perfectly, I've got minecraft running with shaders, etc, and have confirmed my PC is utilising the GPU and use PRIME for switching (not that I ever do):

```
nvidia-driver-440
```

Other than my /var/logs/ folder filling up rapidly, I'm having little issues (touch wood), the only one being once or twice I have encountered a black screen on boot displaying the error over and over.

I've tried editing the grub which has't helped either, and I'm under the impression that noaer and nomsi only "silence" the error?. 

```
sudo gedit /etc/default/grub
```

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer[COLOR=#242729][FONT=Consolas]"
&
[/FONT][/COLOR]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=nomsi"

```

```
 sudo update-grub 
```

I've read about using the following to disable the PCIe Active State Power Management which sounds like it could be related to my issue, but I don't want to keep messing with my grub without really knowing what I'm doing and just following different solutions online hoping something works. 

```

pcie_aspm=off
or
pcie_aspm=force

```

Let me know if you need any more information, I've tried my best to put together what I can.

Hoping for some results soon!

Regards,

---

### Post by CatKiller on 2020-08-10
I don't think it's a problem with the Nvidia side of things. **8086** is Intel's vendor ID. 

> **wizardoveryonder said:**
> I've tried editing the grub which has't helped either, and I'm under the impression that noaer and nomsi only "silence" the error?. 

I have no idea what those options do, particularly, but don't forget to run update-grub after you've changed Grub's configuration for the changes to take effect.

---

### Post by wizardoveryonder on 2020-08-10
*deleted*

---

### Post by wizardoveryonder on 2020-08-11
I had updated grub, so I've updated my original post now. 

Interesting that it's related to Intel.. When I first installed Ubuntu I did not select third party drivers and I never manually installed any drivers for Intel , but I would think if that was the case I would be having bigger issues as the driver for the cpu + on board graphics would be the same.. *hmmmmm*

---

### Post by CatKiller on 2020-08-11
> **wizardoveryonder said:**
> I never manually installed any drivers for Intel

Intel's graphics drivers are open source, so there wouldn't be anything to install. Some Intel wireless chips need proprietary firmware to be loaded.

From your description, though, it's not about either of those, but the chipset: trying to turn things off to save power and not being able to. You'll probably be able to work out which device is actually connected to the PCIe bus that can't turn off - and it *could* be the Nvidia chip that won't let the slot power down, or it could be something else. Power-management is a work-in-progress for Intel. Well, all platforms, really, except maybe ARM.

---

### Post by wizardoveryonder on 2020-08-11
> **CatKiller said:**
> Intel's graphics drivers are open source, so there wouldn't be anything to install. Some Intel wireless chips need proprietary firmware to be loaded. 

I suspected that'd be the case, thanks for clarifying that. :)

> **CatKiller said:**
> You'll probably be able to work out which device is actually connected to the PCIe bus that can't turn off... 

Any suggestions on how I could go about that? Something like lspci? Seeing as though there doesn't _seem_ to be any impact on the system due to the error other than the log files, is there a way I can prevent the error being logged?

---

### Post by CatKiller on 2020-08-11
> **wizardoveryonder said:**
> Any suggestions on how I could go about that? Something like lspci?  
Yep, something like lspci. Seeing which bus each device is connected to, and comparing that with the one that's complaining. 
> Seeing as though there doesn't _seem_ to be any impact on the system due to the error other than the log files, is there a way I can prevent the error being logged?
Probably. I know that there are options to configure the logging level, and there are probably kernel options to specify how much power saving and/or whingeing about power saving should be done, but I don't know enough about either to know what they are.

---

### Post by wizardoveryonder on 2020-08-11
> **CatKiller said:**
> Yep, something like lspci. Seeing which bus each device is connected to, and comparing that with the one that's complaining. 

Alright, I'll look into it and report back. From there I can look into repairing the issue or [COLOR=#000000]configuring the logging level, etc. [/COLOR];)

---

