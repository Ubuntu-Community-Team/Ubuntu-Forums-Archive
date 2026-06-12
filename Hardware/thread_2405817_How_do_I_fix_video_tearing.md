---
title: "How do I fix video tearing"
date: 2018-11-11
forum: Hardware
---

### Post by jacatone on 2018-11-11
Anyone know the command sequence to fix video tearing on an nvidia card?

```
jacatone@OptiPlex-755:~$ lspci -nn | egrep -i "3d|display|vga"
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce 8400 GS Rev. 2] [10de:06e4] (rev a1)
```

---

### Post by Autodave on 2018-11-11
Did you install a driver for this card? If so, what one and where did you get it from?

---

### Post by jacatone on 2018-11-11
Downloaded a ppa for the nvidia drivers. Have an nvidia x settings icon but it won't open. Below is what I have now.

---

### Post by NM5TF on 2018-11-11
post the output of

```
inxi -G
```

have you tried the nouveau driver yet ???

tommy

---

### Post by jacatone on 2018-11-12
Don't know what the nouveau driver is? Here's the command output:

```
jacatone@OptiPlex-755:~$ inxi -G
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: NV98 version: 3.3 Mesa 18.0.5
```

---

### Post by slickymaster on 2018-11-12
*Thread moved to **Hardware**.*

---

### Post by NM5TF on 2018-11-15
> **jacatone said:**
> Don't know what the nouveau driver is? Here's the command output:

```
jacatone@OptiPlex-755:~$ inxi -G
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: x11 (X.Org 1.19.6 )
           [COLOR="#FF0000"]drivers: nouveau[/COLOR] (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: NV98 version: 3.3 Mesa 18.0.5
```

looks like you are already using the nouveau driver....

found this...have not verified personally....

"8xxx series cards only work with 340.96 or lower version of nvidia drivers. To check what version is installed type:

```
nvidia-smi
```

If the driver is above 340.96, try to install an older driver. This particular ppa is good for auto removing and installing:

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-340
```

Restart your PC."

you should see this option in the [COLOR="#FF0000"]additional drivers screen[/COLOR]...try it

hope this helps

tommy

---

### Post by jacatone on 2018-11-17
The additional drivers window just shows a manually installed driver. Should I install this "nvidia-340" driver?

jacatone@OptiPlex-755:~$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

Also found this NVIDIA driver since my install is 64-bit:

[https://www.nvidia.com/object/linux_display_amd64_100.14.09.html](https://www.nvidia.com/object/linux_display_amd64_100.14.09.html)

---

### Post by NM5TF on 2018-11-17
> **jacatone said:**
> The additional drivers window just shows a manually installed driver. Should I install this "nvidia-340" driver?

jacatone@OptiPlex-755:~$ nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

the 340 driver is recommended...try it....use the command sequence above...

tommy

---

### Post by jacatone on 2018-11-18
After installing nvidia-340, my system runs much better, but how do I prevent the NVIDIA X Server Settings window from launching every time I boot up?

---

### Post by NM5TF on 2018-11-18
look in your [COLOR="#FF0000"]startup[/COLOR] app to see if it is listed there...if so, remove it....

tommy

---

