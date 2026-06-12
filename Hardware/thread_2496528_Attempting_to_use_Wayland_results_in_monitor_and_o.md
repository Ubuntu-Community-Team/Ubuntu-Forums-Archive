---
title: "Attempting to use Wayland results in monitor and other problems"
date: 2024-04-01
forum: Hardware
---

### Post by goodstuff9 on 2024-04-01
Ubuntu 22.04, gnome-shell 42.05.  


Three monitors are attached to an Nvidia TU106 GeForce GTX 1650 graphics card, and two monitors are attached to a GA107 GeForce RTX 3050 (6 GB) graphics card.  I'm having very strange problems with this, this stuff is beyond my understanding, 


Under the "Supported Products" tab on this web site, [https://www.nvidia.com/Download/driverResults.aspx/223426/en-us/](https://www.nvidia.com/Download/driverResults.aspx/223426/en-us/) , it says that the two graphics cards I have installed should work with Nvidia's 550.67 driver.  


This web site, [https://9to5linux.com/nvidia-550-67-linux-graphics-driver-brings-wayland-fixes](https://9to5linux.com/nvidia-550-67-linux-graphics-driver-brings-wayland-fixes) , indicates that the 550.67 driver should work with Wayland.  


Here are the problems/issues I'm having:  


A)   When I boot into "Ubuntu" using X11, everything seems to work.  But, when I boot using "Ubuntu Wayland", only the three monitors attached to the GTX 1650 graphics card work, the two monitors attached to the RTX 3050 graphics card are black.  


B)  Both xrandr and ARANDR report a phantom monitor:  In ARANDR it is identified as "None-3-1", and in xrandr "None-3-1" is shown as connected.  (This is in addition to the five monitors.)  


C)  As you can see in the screenshot below all my questions of Ubuntu's "Software & Updates" window, under the "Additional Drivers" tab, the RTX 3050 graphics card is shown to be using the most current 550 series driver - but that graphics card is not properly identified, instead for some strange reason it is listed as "Unknown".  The GTX 1650 graphics card is correctly identified, but the 550 series driver is not even listed as an option.  And as you can see, all drivers for the GTX 1650 graphics card are greyed out, so I can't select any of them for this graphics card.  The only driver that can be used with this graphics card on that tab is something called "Continue using a manually installed driver."  




My questions:  


1)  Why is the RTX 3050 card not properly identified on the "Additional Drivers" tab, and how do I fix that?  


2)  What is the mystery "manually installed driver" on the "Additional Drivers" tab for the GTX 1650 graphics card?  Who installed that driver, and how?  


3)  Why are all the other drivers for the GTX 1650 graphics card greyed out?  How do I enable them to be selected?  


4)  Why is the 550 series driver not even listed on the "Additional Drivers" tab for the GTX 1650 graphics card?  How do I get it to be available for that graphics card as well?  


5)  Why do I have this phantom monitor of "None-3-1", and how do I get rid of it?  


6)  How do I get all five monitors attached to these two graphics card to work under Wayland?  


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293552&stc=1[/IMG]

---

### Post by MAFoElffen on 2024-04-03
Please post the output of this, posted within CODE Tags:
```

sudo lspci -nnnk | grep -A3 -E 'VGA|Display|3D'

```

---

### Post by goodstuff9 on 2024-04-04
> **MAFoElffen said:**
> Please post the output of this, posted within CODE Tags:
```

sudo lspci -nnnk | grep -A3 -E 'VGA|Display|3D'

```


Thanks for responding, and here it is:  

```
main1@system1:~$ sudo lspci -nnnk | grep -A3 -E 'VGA|Display|3D'
[sudo] password for main1: 
00:02.0 Display controller [0380]: Intel Corporation Alder Lake-S GT1 [UHD Graphics 710] [8086:4693] (rev 0c)
    DeviceName: Onboard - Video
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU106 [GeForce GTX 1650] [10de:1f0a] (rev a1)
    Subsystem: PNY TU106 [GeForce GTX 1650] [196e:1400]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
--
06:00.0 VGA compatible controller [0300]: NVIDIA Corporation GA107 [GeForce RTX 3050 6GB] [10de:2584] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8976]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
main1@system1:~$

```

---

### Post by MAFoElffen on 2024-04-05
It says they are recognized and are using the NVidia driver.

What does your /var/log/xorg.0.log say?

---

### Post by goodstuff9 on 2024-04-05
> **MAFoElffen said:**
> It says they are recognized and are using the NVidia driver.

What does your /var/log/xorg.0.log say?

Sorry, I don't know how to interpret all the stuff in that file, so I present it here as a file attachment (*.tar format) hoping you can make some sense out of it.  


[ATTACH]293564[/ATTACH]

---

### Post by MAFoElffen on 2024-04-07
Your NVIDIA GeForce GTX 1650 (TU106-A) at PCI:1:0:0, ID'ed as GPU-0
It is using NVidia driver 550
It has:
 DFP-0 connected to an HP Inc. HP 27 QD
 DFP-1 connected to a BBY NS24D310CA21
 DFP-2 connected to a UPG DP2VGA

Your NVidia GeForce RTX 3050 (GA107-A) at PCI:6:0:0, ID'ed as GPU-1
It is using NVidia Driver 550
It has 
  DFP-1 connected to an Acer S271HL display
  DFP-3 connected to an Acer KA242Y

Those "are" the five displays you said you had connected. But the it gets weird with the RTX 3050.

On that card, a ghost port ID'ed as "none-3-1" does not say if it is connected or not, nor did it find any EDID, BUT on a probe of that port, determied a modeline of 
```

Modeline "1920x1080"x60.0  124.42  1920 1920 1920 1920  1080 1080 1080 1080 (64.8 kHz eP)

```
So (somehow) kept setting up that invalid port.

It did not ID that ghost port as a valid port name, nor could it recognize things there in a manner that makes sense.

I would post that file on the NVidia forum. Seems to me that it is either a problem with the card, or the driver...

^^^ You could rule out a problem with the driver if you uninstalled 550, and installed 540, to see if it has the same error.

---

### Post by #&amp;thj^% on 2024-04-07
Agreed with opting out of driver 550, this is unusal:
```
[  5461.073] (WW) NVIDIA(G0):  - Setting a mode on head 0 failed: Insufficient permissions
[  5461.073] (WW) NVIDIA(G0):  - Setting a mode on head 1 failed: Insufficient permissions
[  5461.073] (WW) NVIDIA(G0):  - Setting a mode on head 2 failed: Insufficient permissions
[  5461.073] (WW) NVIDIA(G0):  - Setting a mode on head 3 failed: Insufficient permissions
[  5461.085] (II) NVIDIA(GPU-0): Deleting GPU-0
[  5461.085] (II) NVIDIA(GPU-1): Renaming GPU-1 to GPU-0
[  5461.085] (II) NVIDIA(GPU-0): Deleting GPU-0
```

With my driver current 
```
 NVIDIA-SMI 550.67                 Driver Version: 550.67         CUDA Version: 12.4 
```
and GPU "NVIDIA GeForce RTX 3050 Ti Mobile" I run more than 2 Displays and I get a lot of tearing and on wayland just a tiny bit better.

And older driver is my second as MAFoElffen suggests.

---

### Post by goodstuff9 on 2024-04-07
Thanks again for helping.  A couple followup questions:  

1) Your last post focused on the ghost port/monitor problem.  Do you think that is related to the other problems I listed in my original post?  

2)  My main concern is why Wayland will not work with these graphics cards and drivers.  I am not married to these particular graphics cards, I'm close to someone who purchases things like used graphics cards, so if I were to replace them, I'd be reimbursed.  My main goal is to be able to have these five monitors working without problems under wayland.  (I am not into gaming.)  So, before I spend a lot of time in an Nvidia rabbit hole, do you know, are there alternative graphics cards I could get that would likely work for what I wish to achieve?  Because then in that case I'd rather just install those alternative graphics cards and related drivers and happily carry on, and just unload the Nvidia stuff.

3)  Where do I find that "Nvidia forum" you're referring to????  When I look at all the forums within "Ubuntu Forums", I don't see anything with that title?  What am I missing?

---

