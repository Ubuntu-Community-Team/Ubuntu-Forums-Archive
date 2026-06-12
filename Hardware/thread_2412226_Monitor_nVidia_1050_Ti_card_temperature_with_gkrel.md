---
title: "Monitor nVidia 1050 Ti card temperature with gkrellm?"
date: 2019-02-09
forum: Hardware
---

### Post by pmaff on 2019-02-09
Hello,

I am trying to monitor the temperature of my nVidia graphic card on my laptop with gkrellm on xfce desktop.

I installed the nVidia drivers for the nVidia graphic card 1050 Ti on the laptop from
[https://www.nvidia.de/Download/index.aspx?lang=de](https://www.nvidia.de/Download/index.aspx?lang=de)

After some tweaks with missing links I got xscreensaver to work.
The remaining problem is, that nvidia-settings is working remote via ssh on my desktop where it shows the graphic card and monitor of the desktop (of course)
but not when started on the laptop.
There I get
"ERROR: Unable to load info from any available system"

The laptop is one with dual graphic cards (Intel and nVidia) and according to the hardware LED it uses the nVidia graphics.
I have not installed bumblebee or similar since I want to use the nVidia and not the Intel.
journalctl | grep "Loading NVIDIA Kernel Mode Setting Driver for"
gives a correct
"...kernel: nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  410.93  Thu Dec 20 16:59:23 CST 2018"

nvidia-smi -q -d temperature shows:
==============NVSMI LOG==============

Timestamp                           : Sun Feb 10 00:41:57 2019
Driver Version                      : 410.93
CUDA Version                        : 10.0

Attached GPUs                       : 1
GPU 00000000:01:00.0
    Temperature
        GPU Current Temp            : 40 C
        GPU Shutdown Temp           : 102 C
        GPU Slowdown Temp           : 97 C
        GPU Max Operating Temp      : 94 C
        Memory Current Temp         : N/A
        Memory Max Operating Temp   : N/A

What is missing to make nvidia-settings working on the laptop with the laptop monitor and the 1050 Ti?
As far as I remember nvidia-settings can then be used to monitor  temperature of the graphic card with gkrellm, which I already use to  monitor the CPU temperature (lmsensors)
and the harddisk temperature (hddtemp).
I got this to work already on my old laptop with SuSE and KDE but the  old one had only one graphic card so I assume that that is the reason.
Do I have to tell nvidia-settings which graphic card is used?


Excuse my bad English as this is not my mother language.

Thanks in advance.
Pete

---

### Post by pmaff on 2019-02-12
Bump

---

