---
title: "NVIDIA GTX 1060 drivers on Ubuntu 16.04 LTS"
date: 2017-12-13
forum: Hardware
---

### Post by m2p5 on 2017-12-13
Hello, I’m trying to install a NVIDIA GTX 1060 on Ubuntu 16.04 LTS and I’m having some trouble. First after a clean installation of Ubuntu I’ve installed the NVIDIA drivers. The installation seemed to be successful, but the computer started to “freeze” randomly. Tried some solutions but none worked so I’ve redone a fresh installation of Ubuntu. This time didn’t install the NVIDIA drivers and the computer never froze again but the other day after a reboot the monitor display didn’t show anything and since then I’ve tried to reboot a couple times and still no display. It doesn’t even show the initial screen on boot to enter bios. However, the computer is running, and I can use it normally with ssh or teamviewer so I believe the issue is in the graphics card driver (currently the default driver, nouveau, is installed).

Additional information: 
When I did the new fresh Ubuntu installation I had to power on and off the computer a couple of times because no image was displaying. Possible it was turning on, but I had no way to tell since I hadn’t enabled ssh yet. But then eventually the monitor started to display, and I was able to install the system without any problem. It had been running for 2 or 3 days and everything okay with the display, only after rebooting it blacked out.

I don’t know if this information helps but the command “sudo lspci -vnn | grep VGA -A 12” gives:
65:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c02] (rev a1) (prog-if 00 [VGA controller])
                Subsystem: Gigabyte Technology Co., Ltd Device [1458:3724]
                Flags: bus master, fast devsel, latency 0, IRQ 50
                Memory at d7000000 (32-bit, non-prefetchable) [size=16M]
                Memory at c0000000 (64-bit, prefetchable) [size=256M]
                Memory at d0000000 (64-bit, prefetchable) [size=32M]
                I/O ports at b000 [size=128]
                Expansion ROM at 000c0000 [disabled] [size=128K]
                Capabilities: [60] Power Management version 3
                Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Capabilities: [78] Express Legacy Endpoint, MSI 00
                Capabilities: [100] Virtual Channel
                Capabilities: [250] Latency Tolerance Reporting


Thanks in advance!

---

### Post by Autodave on 2017-12-13
What driver did you install and where did you get it from?  The safest way is to go to ADDITIONAL DRIVERS and install the recommended one. Do NOT install from the Nvidia site.

---

### Post by Yellow Pasque on 2017-12-13
> It doesn&#8217;t even show the initial screen on boot to enter bios.

That suggests a hardware problem. If you're able to try the video cable and monitor on another system, do so.

---

### Post by m2p5 on 2017-12-14
> **Autodave said:**
> What driver did you install and where did you get it from? The safest way is to go to ADDITIONAL DRIVERS and install the recommended one. Do NOT install from the Nvidia site.

I installed from Nvidia site, didn't know about the "additional drivers" menu. But then I did the clean reinstall of Ubuntu so it went back to the defaults. I've already tried to install it by the "additional drivers" menu but it didn't solve the black display problem and the image on teamviewer disappeared after reboot (just showed a black screen on teamviewer), I had to uninstall it by ssh.


> **Temüjin said:**
> That suggests a hardware problem. If you're able to try the video cable and monitor on another system, do so.

I have just tried the video cable and monitor on another system and it works fine. Can it be a problem with the graphics card itself?

---

### Post by Autodave on 2017-12-14
That is always a possibility.

What cable are you using: DVI or HDMI or ??

---

### Post by m2p5 on 2017-12-14
I'm using a DVI. I don't have here a HDMI to try but I will borrow one to try tomorrow.

---

### Post by m2p5 on 2017-12-15
Update: HDMI cable didn't work but then I took off the graphics card and put it back in the same slot and the display started to work. However, when I turned the pc back on after closing and putting the pc in the vertical position, the display didn't show anything again. I repeated the process and it's now working but with the pc in horizontal position. It seems to me that it may be a bad connection caused by the graphics card own weight.

**Edit**: I've installed the NVIDIA drivers using the "additional drivers" tool and after a while the computer "froze" again.

---

### Post by Autodave on 2017-12-15
I believe that you need to fix the hardware problem first.  Possible bad graphics card or motherboard are the most likely culprits.  I would start by turning the PC off and then going through every cable and connector. Remove and install every one of them and see what that does.

---

### Post by Autodave on 2017-12-15
Thought of another possibility: while you have the side off of the 'puter, check to see what the power supply is rated at: wattage total.  Also, how many USB devices do you have hooked up to the machine?

---

### Post by Yellow Pasque on 2017-12-15
I'd also be checking the temps:
```
sensors
nvidia-smi
```

---

### Post by sccman on 2017-12-15
Another possibility: Is the graphics card secure in the PCI Express slot? Make sure that the GPU snaps all the way into the slot and that the screw is tight in the mounting bracket. If a GPU is jiggling while in use it could make the screen black out/freeze.

---

### Post by m2p5 on 2017-12-18
> **Autodave said:**
> Thought of another possibility: while you have the side off of the 'puter, check to see what the power supply is rated at: wattage total. Also, how many USB devices do you have hooked up to the machine?
It's a 850W psu. Just the mouse and keyboard.

> **Temüjin said:**
> I'd also be checking the temps
The cpu temps are good. I've uninstalled nvidia drivers so I can't use the nvidia-smi command now.

> **sccman said:**
> Another possibility: Is the graphics card secure in the PCI Express slot? Make sure that the GPU snaps all the way into the slot and that the screw is tight in the mounting bracket. If a GPU is jiggling while in use it could make the screen black out/freeze.
I think this is at least part of the problem. Actually, the computer arrived with no screws on the graphics card mounting bracket. I screwed it but maybe it's not enough. The fact that (with nouveau driver) it works with the pc on the horizontal (so no tension on the pcie slot caused by the graphics card weight) but it fails to display with the pc on the vertical position, seems to me good evidence supporting that.

I will try as soon as possible to test another graphics card and also test this one on another machine. Thanks all for the help so far, I will post an update as soon as I do these tests.

---

### Post by tokyobadger on 2017-12-18
As noted by Temüjin if you're getting a blank screen at the BIOS screen video drivers are not the issue (not loaded yet).

If the cable and the monitor work on another PC and you have intermittent video signal everything points to a connection issue between PCIe slot, gfx card, or gfx card and video cable, most likely the former if you have consistent success when the PC is horizontal; the newer cards are quite heavy and should definitely be screwed in place (not too hard but firmly).

Do you have another PCIe slot you could try on the motherboard? 

Are the slots clean?

Is the gfx card's connector clean?

Have you tried another of the ports on the back of the card with the DVI cable?

Once you can consistently get a video signal at BIOS while the PC is vertical, then you can look into the nvidia driver topic.

---

