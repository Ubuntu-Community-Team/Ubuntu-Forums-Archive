---
title: "Graphic support"
date: 2019-11-24
forum: Hardware
---

### Post by RobGoss on 2019-11-24
Hello everyone can anyone tell me which graphic cards are best supported for Linux / Ubuntu

Brand names as well.. I got a machine from my son and it has a **Vapor X** graphics card in it but I seem to have issues using it with a new monitor

This is my graphic card info

```
lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
```

is this graphic card suitable for Ubuntu? it was working just fine but when i use this new monitor I have issues like screen tearing

Thanks so much

---

### Post by TheFu on 2019-11-24
Intel iGPUs are the best supported.  i915.
I don't know if stand-alone Intel GPUs are sold.  They are built into many desktop/laptop Intel CPUs.

Lacking that, AMD and nVidia from 1-3 yrs ago are probably the best choices. Nothing just released.  I have an nVidia 1030 GT.  Since I'm using only LTS releases, [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its) applies.  Before that change, there were times I'd wished I'd gotten an AMD GPU instead.

---

### Post by RobGoss on 2019-11-24
Thanks so much, did you see the specs for my card? is it ok with Ubuntu?

My son had this machine built so I don't know much about it. It looks like a AMD graphic card

---

### Post by TheFu on 2019-11-24
> **RobGoss said:**
> Thanks so much, did you see the specs for my card? is it ok with Ubuntu?

My son had this machine built so I don't know much about it. It looks like a AMD graphic card

I'm not up on AMD GPUs or bleeding edge nVidia cards. My last Radeon GPU was in the 54xx line when AMD stopped making Linux drivers, but before nouveau was available. It was pre-h.264/mpeg2 built-in support, I think.  Sorry.

---

### Post by CatKiller on 2019-11-24
> **RobGoss said:**
> Hello everyone can anyone tell me which graphic cards are best supported for Linux / Ubuntu 

As TheFu says, Intel is the most painless. With the exception of very old stuff that they licenced from PowerVR their drivers have been open source and part of the normal graphics stack since the very beginning, and they have vast resources to put to making them work as well as they can. The actual performance of their integrated graphics is limited by the strength of the actual hardware. They don't make dedicated graphics cards, although they are expected to do so in the next year or so. They have already laid the groundwork for that in the open source graphics stack. 

Nvidia's drivers are proprietary (closed source) and are not part of the normal graphics stack. Their Linux drivers match the features and performance of their Windows drivers and, largely because of that, they do entirely their own thing, which causes friction with what everyone else is doing. The performance of their highest-end hardware is higher than that of the other GPU makers, and their driver is generally able to extract all of that performance, although newer hardware needs a newer driver than is usually available from the standard repositories. When it works, it's generally quite straightforward. An Optimus setup, common with laptops, of having both Nvidia and Intel graphics, is an absolute pain and is generally best avoided. 

AMD's hardware is generally in-between the other two. They used to have a proprietary driver but abandoned that in favour of using the open source one. Because they have limited resources, the software side of things is rarely in place before the hardware is released. Getting newer versions of the software generally means upgrading the entire graphics stack. Performance of their driver can vary significantly relative to their Windows driver for the same hardware. 

> is this graphic card suitable for Ubuntu? 

It should be perfectly fine, although I understand that there are some tweaks that you need to do if you want to use Vulkan with older AMD cards. 

>  it was working just fine but when i use this new monitor I have issues like screen tearing

High refresh rates and variable refresh rates, both of which are common with newer monitors, are non-trivial problems to solve. Work is happening on that front, but I understand that it's still got a way to go.

If you'd like assistance with the screen tearing issue it would be best to start a new thread about that with a descriptive title, and include details of the monitor, how it's connected, which version of Ubuntu you're using, and which desktop environment, so that someone who knows about that will be able to take a look.

---

### Post by oldfred on 2019-11-24
Do not know AMD.

This said update to UEFI resolved his issue of blackscreen.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1796574](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1796574)

Some comparisons:
[https://www.phoronix.com/scan.php?page=article&item=gcn10-tww2-radv&num=2](https://www.phoronix.com/scan.php?page=article&item=gcn10-tww2-radv&num=2)

Mentions AMDGPU and mesa drivers:
[https://forum.level1techs.com/t/amd-r9-280x-linux-gaming-support/137021/13](https://forum.level1techs.com/t/amd-r9-280x-linux-gaming-support/137021/13)
[http://ubuntuhandbook.org/index.php/2018/05/install-mesa-18-0-4-ubuntu-18-04-lts/](http://ubuntuhandbook.org/index.php/2018/05/install-mesa-18-0-4-ubuntu-18-04-lts/)

---

