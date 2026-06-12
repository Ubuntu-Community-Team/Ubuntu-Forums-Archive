---
title: "Unkown display,xrandr badmatch,resolution undetected."
date: 2016-10-01
forum: Hardware
---

### Post by frojin on 2016-10-01
Hi,
I am fairly new to ubuntu (and linux in general) so I just installed it, and it doesn't recognize my monitor, just says "unknown display", so I tried to add a resolution with xrandr but I keep getting this message.
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38


```
I hope I am also using the forums right.

---

### Post by DuckHook on 2016-10-01
*Thread moved to **Hardware** as the more appropriate forum.*

Welcome to the forums, frojin.

You are using the forums correctly, especially after obviously doing some research and trying to solve the problem yourself first.

Please post results from the following:
```
xrandr
``````
lspci -vk | grep -iA15 vga
``````
sudo apt install read-edid && sudo get-edid | parse-edid
```The last instructions will download an app from the repos that can read your monitor edid info if it is, in fact, readable. You will have to authenticate with your password to allow the app to download.

When asking about HW issues, it is necessary to post as much info as possible.

[LIST=1]
[*]Computer make/model/specs?
[*]Monitor make/model/specs (especially native resolution)?
[*]Do you use a KVM switch?
[*]What cabling? HDMI? VGA? DP? Are there cable converters?
[*]Please post the actual string and commands you used to try and set xrandr
[/LIST]

---

### Post by frojin on 2016-10-01
xrandr:
```
Screen 0: minimum 8 x 8, current 1152 x 864, maximum 16384 x 16384
DVI-I-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96    59.80  
   1152x864      60.00* 
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)


```

lspci -vk | grep -iA15 vga:

```
0f:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd GM107 [GeForce GTX 750 Ti]
    Physical Slot: 2
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at e0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at e3080000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_361

0f:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device 36ca
    Physical Slot: 2

```

sudo apt install read-edid && sudo get-edid | parse-edid :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
read-edid is already the newest version (3.0.2-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
I'm sorry nothing was successful. Maybe try some other arguments
if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.
Partial Read... Try again


```

1. It's an an HP workstation, intel xeon processor, nvidia geforce GTX 750 Ti GPU.
2.I don't really know...It's samsung but native resolution is 1600x900 with 60hz refresh rate.
3.no.
4.I think it's VGA cable but there is a converter to DVI just at the graphics card.
5.```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode DVI-I-0 1600x900_60.00


```
 and that's where I get the badmatch error..

---

### Post by DuckHook on 2016-10-01
Your system cannot read your monitor's edid. This is why the system doesn't know your monitor capabilities and defaults to those strange lower resolutions. The converter may be to blame. Try connecting the monitor up to the corresponding port of the graphics card using straight VGA to VGA or DVI to DVI. In other words, don't convert the signal. The converter may be blocking your edid data.

How did you get your mode line? This is very important, so please give us all the steps you took, and/or point us to the references you followed.

---

### Post by efflandt on 2016-10-02
Linux cannot tell what your display is capable of when using VGA (analog video) like it can with digital video (DVI-D or HDMI). It looks like the modeline was obtained using cvt (an alternate method is gtf). Any xrandr command used to throw an error for nvidia drivers, but it at least displays existing modes now. I have only manually set modes with xrandr for Intel and legacy ATI graphics and not Nvidia. I cannot test manually setting VGA modes right now.

I am using DVI to HDMI cable for my MSI GTX 750 Ti which automatically recognized 1080p screen resolution (it also has separate VGA and HDMI ports). But I think its DVI is just DVI-D because xrandr does not show any DVI-I device.

---

### Post by DuckHook on 2016-10-02
> **efflandt said:**
> Linux cannot tell what your display is capable of when using VGA (analog video) like it can with digital video (DVI-D or HDMI).  I have successfully retrieved edid with many VGA setups. But a good cable is key. Some VGA cables are missing the wires/pins needed to pass the data. Converters are especially problematic.> It looks like the modeline was obtained using cvt (an alternate method is gtf).I suspected this but wish the OP's confirmation.>  Any xrandr command used to throw an error for nvidia drivers, but it at least displays existing modes now. I have only manually set modes with xrandr for Intel and legacy ATI graphics and not Nvidia. I cannot test manually setting VGA modes right now.

I am using DVI to HDMI cable for my MSI GTX 750 Ti which automatically recognized 1080p screen resolution (it also has separate VGA and HDMI ports). But I think its DVI is just DVI-D because xrandr does not show any DVI-I device. Analog ports are quite capable of providing edid and I have successfully retrieved them through nVidia cards as well. There is usually some combo of ports and wires that gum up the works, but nothing that inherently prevents such readings.

@OP

Please provide the requested info and then we can go to the next steps.

---

### Post by frojin on 2016-10-02
Yes, I used cvt with my screen dimensions.

I am just looking for a DVI-D(dual link) cable..It's the only common port between the screen and the graphics card..most nearby stores don't have it, so I am still looking around so it might take some time.

---

### Post by frojin on 2016-10-02
It worked.
The system recognized my screen and changed the resolution automatically to 1600x900.
Thanks for the help, I probably would have not suspected the converter for at least a month, thank you so much.

---

### Post by DuckHook on 2016-10-02
Great! Glad things worked out.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

