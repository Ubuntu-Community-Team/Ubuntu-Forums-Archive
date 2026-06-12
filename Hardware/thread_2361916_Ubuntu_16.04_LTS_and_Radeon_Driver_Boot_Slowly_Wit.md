---
title: "Ubuntu 16.04 LTS and Radeon Driver Boot Slowly Without nomodeset"
date: 2017-05-22
forum: Hardware
---

### Post by g00d-fabio-r00t on 2017-05-22
Hi All
I have successfull installed Ubutu **16.04.02 LTS **on Asus Laptop with AMD Processor with **Hybrid Graphic Card**.
The Graphic cards are **HD 7470M **(Discrete Card) which is support by Radeon open source driver and **HD 6320 **(integrated card)

The only way to complete the installation is insert kernel boot parameter in grub configuration "n**odomeset"**, the side effect is that the only Display resolution at the end of intallation is:
1024x768 (with unknown display) and poor graphic performance.
I have successfull installed Objaf driver but the OpenGL is alway 3.0 and nothing it's changed.

I have try to boot wihtout Kernel Paramter "nomodeset" and after these unresolved message:

1. **scanning for btrfs file system**
2. [B]Task plymouthd:365 blocked  for more than 120second
    not tainted 4.8.0-52 generic #55 16.04.1-ubuntu[/B]

... repetead for 4/5 times, the boot sequence and ubutu\gnome goes well, the resolution is correct (1733x768), the graphic performance are optimal! 
I think that the kernel "switch?" to the discrete ghaphic card (that is supported) and all goes fine

In another tentative, with 1024x768 resolution active i try to force **modeprobe radeon.modeset=1,** the system kill X Session and i receive "[B]waiting for xserver to begin accepting connections"
[/B]
How can resolve this? For me It's ok using always one graphic card (HD7470M beacause the notebook battery is gone ^_^) 

Many Thanks for attention
Fabio!

---

### Post by g00d-fabio-r00t on 2017-05-24
Anyone can help me? or have a suggest?

---

### Post by Yellow Pasque on 2017-05-24
[https://wiki.ubuntu.com/Plymouth#Debugging](https://wiki.ubuntu.com/Plymouth#Debugging)

---

### Post by g00d-fabio-r00t on 2017-05-25
Thanks for the link [**[COLOR=#000000]Temüjin[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")
Here there are some updates:

1.After 21 minutes for bootingn (nomodeset in grub) , this is the ghraphic card state (optimal performance) (attach image P1)

2. The 21 minutes are due to plymouth (attach image P2)

After some investigations, i disable the splash screen removing "quiet splash" from grub2

3. After this modify, the boot show attach image P3


Now i'm searching a way (i hope exists) that detect correctly (and without 21 minutes to boot) the GPU.
How can modify the job that start for detect the avaiable GPUs?

Thanks

---

### Post by g00d-fabio-r00t on 2017-05-27
Hi All 
Update, here there are syslog messages of two boot sequence, the first is without option in grub and during 21 minutes:

[https://paste.ubuntu.com/24679924/](https://paste.ubuntu.com/24679924/)

This instead is the boot sequence with radeon.modeset=0 which is normal fast but the resolution is poor and the display settings unmanged because the dispaly is view as "unknown"

[https://paste.ubuntu.com/24679971/](https://paste.ubuntu.com/24679971/)

---

### Post by g00d-fabio-r00t on 2017-05-28
Someone can Help me? 
There is a way to save the radeon gpu detected? The boot goes fine after 21 minutes, radeon can rember this configuration for EVER, and not detect the GPU at every boot?

Unfortunately in the bios of ASUS X53BR-SX013V, already updated to 2.10v, there isn't the option to disable the graphic card.

I have tried this:
fbcon=map:0 without radeon.modeset=0 on grub cmd line  but nothing change, always 21 minutes

I have found "AMD Radeon HD 6300 Series Graphics" (ChipID = 0x9806)" but how can force radeon module to using only this IGD?

---

