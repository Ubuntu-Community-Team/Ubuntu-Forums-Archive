---
title: "Screen resolution problems in Ubuntu Mate 16.04 AMD64 on laptop with quadcore AMD A6."
date: 2016-10-12
forum: Hardware
---

### Post by GwibberFooey on 2016-10-12
I am having screen resolution problems in Ubuntu Mate 16.04 AMD64. My computer is a Samsung laptop with quadcore AMD A6 processors.

All output onscreen is distorted in such a way that is stretched laterally, or equivalently, compressed vertically. The monitor hardware is widescreen therefore it should have 16:9 resolution (ie. 1366:768). 

When I run the command ```
sudo xrandr -q
``` in terminal then I receive the following output:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       0.00*
```

When I run the command ```
sudo cvt 1366 768
``` in terminal then I receive the following output: 
```
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
```

And when I run the command ```
sudo xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
``` in terminal then I receive the following output:
```
xrandr: Failed to get size of gamma for output default
```

If somebody can offer some instructions for how to force this system to display with the correct screen resolution then I will thank you very much.

---

### Post by #&amp;thj^% on 2016-10-12
You shouldn't need sudo to register the new mode with xrandr, try without sudo. Then you'll have to apply the new resolution with:
Just an example
```
xrandr --addmode <your_connection_type> 1200x1000_60.00

```
Where <your_connection_type> is usually VGA1, DP1 or HDMI1. Check the output of xrandr to know the exact name of the connected output.

---

### Post by GwibberFooey on 2016-10-12
When I run the command ```
xrandr -q
``` then I receive the output ```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       0.00* 
  1368x768_60.00 (0x2c0) 85.250MHz -HSync +VSync
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock  47.79KHz
        v: height  768 start  771 end  781 total  798           clock  59.88Hz
```

xrandr seems to be unable to determine the <my_connection_type>. Do you know any other way to get this information?

---

### Post by #&amp;thj^% on 2016-10-12
Well that's not good.
Maybe try this
```
xrandr --query
```
EDIT or even this
```
xrandr --listactivemonitors

```

---

### Post by GwibberFooey on 2016-10-12
```
xrandr --query
``` yields exactly the same output as does ```
xrandr -q
```

Furthermore. When I run the command ```
xrandr --listactivemonitors
``` then I receive the following output:
```
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +default 1024/271x768/203+0+0  default
```

---

### Post by #&amp;thj^% on 2016-10-12
> **GwibberFooey said:**
> ```
xrandr --query
``` yields exactly the same output as does ```
xrandr -q
```

You are right...Hehe need more coffee:)
Well try this one then
```
xrandr --listactivemonitors
```

---

### Post by GwibberFooey on 2016-10-12
When I run the command  ```
xrandr --listactivemonitors
```  then I receive the following output:
```
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +default 1024/271x768/203+0+0  default
```

---

### Post by #&amp;thj^% on 2016-10-12
If we try hard enough...we might get something to give it up.
```
lspci -vnn | grep VGA -A 12
```
And I am assuming here that you are fully updated...just checking is all.
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```

---

### Post by GwibberFooey on 2016-10-12
Firstly: I run (as sudo) ```
apt-get update
``` and ```
apt-get upgrade
``` regularly and I did so less than 3 hours ago. I have not run ```
apt-get full-upgrade
``` because according to my understanding - and please correct me if I am wrong - ```
apt-get full-upgrade
``` does the same as ```
apt-get dist-upgrade
```, and ```
apt-get dist-upgrade
``` would upgrade[sic] my system from Ubuntu Mate 16.04 LTS to Ubuntu Mate 16.10, which I don't necessarily want.

Now. What follows is the output from ```
lspci -vnn | grep VGA -A 12
```
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd BeaverCreek [Radeon HD 6520G] [144d:c609]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at a0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: radeon

00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
    Flags: bus master, fast devsel, latency 0, IRQ 26
--
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Radeon HD 7470M [144d:c609]
    Flags: fast devsel, IRQ 10
    Memory at b0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at fea20000 (64-bit, non-prefetchable) [disabled] [size=128K]
    I/O ports at e000 [disabled] [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [144d:c608]
    Flags: bus master, fast devsel, latency 0, IRQ 24
```

---

### Post by #&amp;thj^% on 2016-10-12
> **GwibberFooey said:**
>  my system from Ubuntu Mate 16.04 LTS to Ubuntu Mate 16.10, which I don't necessarily want.

No it won't take you to a different or higher version it just fully updates your current system so i would give that a shot first. IE:16.04 (I think you are thinking of "sudo do-release-upgrade")
But looking at this "[Radeon HD 6520G]" I am not sure how well this is supported on 16.04 as the driver is now like Intel...it is in the installation now.
I need to do some checking here on that GPU. I have nothing but Nvidia on my system.
BTW have you checked in Additional Drivers in synaptic yet to see if by chance there was something needed to install?

---

### Post by #&amp;thj^% on 2016-10-12
I quote this from QIII
> Yes. AMD calls this a "dual GPU" arrangement rather than the hybrid Intel/AMD system.
If you were able to run fglrx (which you can't with 16.04), you would be able to initialize both GPUs. Here, I suspect oldfred is right: disable one or the other in BIOS. You'll likely have to insert the Radeon module manually, but we can help you with that after you tell us you can disable one of the GPUs.

And the poster replied with this
> after from BIOS- Settings-Display- I changed switchable graphics to integrated graphics here and ubuntu booted normally without any problems after a week of effort its finally over Thank you everyone for your support.

Source: [https://ubuntuforums.org/archive/index.php/t-2329295.html](https://ubuntuforums.org/archive/index.php/t-2329295.html)
So there is hope.

---

### Post by GwibberFooey on 2016-10-12
Yes, I recall having read that AMD has ended their support for the Catalyst\fglrx driver. As I am running Ubuntu (Mate) 16.04 AMD64, therefore I understand that my system is running via the open-source driver (I think it is called amdgpu). I would believe it if somebody told me that the display problems I am currently having are a consequence of the transition to the new driver. But I don't know enough about Linux OS and microcomputer architecture to be able to do much about it.

Furthermore. My system is now fully upgraded after having run ```
sudo apt-get full-upgrade
```

---

### Post by #&amp;thj^% on 2016-10-12
> **GwibberFooey said:**
> Yes, I recall having read that AMD has ended their support for the Catalyst\fglrx driver. As I am running Ubuntu (Mate) 16.04 AMD64, therefore I understand that my system is running via the open-source driver (I think it is called amdgpu). I would believe it if somebody told me that the display problems I am currently having are a consequence of the transition to the new driver. But I don't know enough about Linux OS and microcomputer architecture to be able to do much about it.

Furthermore. My system is now fully upgraded after having run ```
sudo apt-get full-upgrade
```

Maybe a reboot might be needed..(No Promises though)
And if you get bored...you may find you are not alone.
Gosh I hate reporting things like this:[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
More here:[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1)

[https://hashcat.net/forum/thread-5410.html](https://hashcat.net/forum/thread-5410.html)

---

### Post by QIII on 2016-10-12
Just a technical note:

If running on the HD 6XXX series GPU, the open source Radeon driver would have been installed, not the open source AMDGPU driver.

AMDGPU is only installed when GPUs with physical GCN support are present.  HD 6XXX cards are not GCN cards.

AMDGPU is installed (right now) only if a GCN 1.2 GPU is present, and it can be experimentally installed with a GCN 1.1 card.  Support for GCN 1.0 cards is being developed.  In case you are wondering, GCN 1.0 appears first in select HD 7XXX GPUs.  So AMDGPU (and the AMDGPU-Pro driver, which is the open source AMDGPU base with the proprietary binary on top) will only ever work with HD 7XXX cards and later.

All other GPUs will use the open source Radeon driver.

You can confirm this by:

```
lsmod | grep radeon
```

which should return several lines and

```
lsmod | grep amdgpu
```

which should return nothing.

---

### Post by GwibberFooey on 2016-10-12
In my case, both of the commands that you presented returned nothing.

---

### Post by QIII on 2016-10-12
Ok, then.  Go to the suggestion about disabling one of the GPUs and let's see if we can't make something happen on reboot.

---

### Post by #&amp;thj^% on 2016-10-12
> **GwibberFooey said:**
> Yes, I recall having read that AMD has ended their support for the Catalyst\fglrx driver. As I am running Ubuntu (Mate) 16.04 AMD64, therefore I understand that my system is running via the open-source driver (I think it is called amdgpu). I would believe it if somebody told me that the display problems I am currently having are a consequence of the transition to the new driver. But I don't know enough about Linux OS and microcomputer architecture to be able to do much about it.

Furthermore. My system is now fully upgraded after having run ```
sudo apt-get full-upgrade
```
If you ran that exact code....I am not sure it did anything.
The code would be...and your choice here
```
sudo apt full-upgrade
<or>
sudo apt-get dist-upgrade
```
Again they will not take you to a newer version just fully up-grade your existing OS.(16.04)


@QIII Thanks for the update (technical note).:)

---

### Post by GwibberFooey on 2016-10-12
Currently my ```
/etc/default/grub
``` file contains a line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```. I had found when I installed Ubuntu Mate 16.04 AMD64 LTS that I was having blankscreen problems unless I boot-up as with nomodeset.
Could this be the reason why both ```
lsmod | grep radeon
``` and ```
lsmod | grep amdgpu
``` return nothing?

---

### Post by GwibberFooey on 2016-10-12
I had a similar experience (ordeal) one year ago when I installed Ubuntu 14.04 LTS onto this very same laptop computer.  [https://ubuntuforums.org/showthread.php?t=2297945](https://ubuntuforums.org/showthread.php?t=2297945)  At that time, the remedy was to install fglrx\Catalyst via the command ```
sudo apt-get install fglrx
``` and to fix the ```
/etc/default/grub
``` file by removing the term "nomodeset" from the file. 

I think that the solution to my current problem is the same. But here is the question: what driver should I be trying to install now? And what command can I use to install it?

---

### Post by QIII on 2016-10-12
Don't try fglrx.  It will not work with the X Server version that comes with 16.04, which is why it is not included in the repo.

We need to get your machine to load the radeon module, which may happen if you disable one of the GPUs in your BIOS/UEFI.  If not, we can modprobe it in.

---

### Post by GwibberFooey on 2016-10-13
I can confirm that package xserver-xorg-video-amdgpu version 1.1.0-1 is currently installed. But how can I force my machine to load the radeon module?

---

### Post by QIII on 2016-10-13
Have you gone to your BIOS/UEFI, disabled the dedicated GPU and rebooted?

---

### Post by GwibberFooey on 2016-10-13
I looked around in the BIOS but there is no obvious way for me to disable the dedicated GPU.

---

### Post by GwibberFooey on 2016-10-13
Is there a way to use modprobe to achieve the desired result?

---

