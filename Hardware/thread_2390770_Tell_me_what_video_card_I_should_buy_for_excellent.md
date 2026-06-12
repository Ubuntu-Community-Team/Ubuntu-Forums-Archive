---
title: "Tell me what video card I should buy for excellent 4K monitor support for 18.04"
date: 2018-05-02
forum: Hardware
---

### Post by alexpirine on 2018-05-02
Hi,

This is my first message in ubuntuforums.org but I've been an Ubuntu user since a very long time.

The issue is that I'm not using the desktop version since about 10 years.

And things seem to have changed, and I see some issues I'm not able to resolve on my own.

I have an AMD Ryzen computer, so I need a separate video card.

I also have a 4K monitor, so I need the UI to scale correctly.

Has anyone been able to do it? Just tell me what is **the best** thing to buy, that just **works**.

I don't play video games, I just need something that works without lags when I scroll and without system freezes…

If you have a setup that just works, I will highly appreciate if you can share!

Thank you very much,

Alex

P.S. I currently have an nvidia GT 1030… With a fresh 18.04 install, the system was very unresponsive. So I installed the proprietary drivers. With proprietary drivers it works, but the scaling can only be changed from 100% (I'm barely able to read text) to 200% (I don't have much space). Also when I scroll in Chrome, the GPU turns to 100% and I see lags. Sometimes the system freezes completely and I have to reboot.

---

### Post by Autodave on 2018-05-03
Wgat driver are you using and where did you get it from? 390.48 looks like the most recent driver. Your card is showing 2G memory, so that should be enough for regular viewing even at 4K resolution. Gaming would be another story though at that resolution.

---

### Post by pqwoerituytrueiwoq on 2018-05-03
If you do not know just run the [FONT=courier new]nvidia-smi[/FONT] command and post the output
If you want a auto refresh on it here is a tiny script:
[FONT=courier new]nvidia-usage='while [ 1 ];do a="$(nvidia-smi)";clear;echo "$a";sleep 1;done'[/FONT]
if it is getting worked hard it's memory may be maxed out and/or you will see the temp high on it and it will show the driver version

---

### Post by alexpirine on 2018-05-04
Here is my `nvidia-smi` output:

```
# nvidia-smi
Fri May  4 13:34:43 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.48                 Driver Version: 390.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 1030     Off  | 00000000:07:00.0  On |                  N/A |
| 35%   38C    P0    N/A /  30W |   1347MiB /  1998MiB |     29%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1415      G   /usr/lib/xorg/Xorg                            40MiB |
|    0      1477      G   /usr/bin/gnome-shell                          48MiB |
|    0      3442      G   /usr/lib/xorg/Xorg                           600MiB |
|    0      4376      G   /usr/bin/gnome-shell                         239MiB |
|    0      9785      G   ...-token=FB584B03F6D3136D2534CE9E3DAE3275   356MiB |
|    0     24584      G   ...-token=C3E12CF56D3601A487E809DC84B463B0    60MiB |
+-----------------------------------------------------------------------------+

```

If I look at a 1080p video x2 speed on YouTube, I see frame drops and it is sluggish.

```

Fri May  4 13:38:36 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.48                 Driver Version: 390.48                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 1030     Off  | 00000000:07:00.0  On |                  N/A |
| 35%   46C    P0    N/A /  30W |   1758MiB /  1998MiB |     43%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1415      G   /usr/lib/xorg/Xorg                            40MiB |
|    0      1477      G   /usr/bin/gnome-shell                          48MiB |
|    0      3442      G   /usr/lib/xorg/Xorg                           664MiB |
|    0      4376      G   /usr/bin/gnome-shell                         474MiB |
|    0      9785      G   ...-token=FB584B03F6D3136D2534CE9E3DAE3275   467MiB |
|    0     24584      G   ...-token=C3E12CF56D3601A487E809DC84B463B0    60MiB |
+-----------------------------------------------------------------------------+

```

I appreciate your help with my issue, but I'm really unsure if there will be an easy fix, so could you please share your config if everything works fine for you?

---

### Post by pqwoerituytrueiwoq on 2018-05-04
Well you are not out of vram, you do not have much left, but as long as your not out you are good; definitely not gonna run xonotic on with all the setting maxed out (not at 4k anyway)
gpu temperatures are good so it is a very very long way from throttling and you are only using it at 30% (i doubt a gt 1030 can throttle without a heating element next to it)
how does the cpu usage look? any cores maxed out?
have you tested it on a different DE like xfce, kde, or lxde/lxqt (Looks like you are using gnome)

if you still think it is the GPU you could try it in performance mode, it is clearly is not under a high load so it still has more to offer
[URL="http://i.imgur.com/8R9Nw51.png"]
  [IMG]http://imgur.com/8R9Nw51l.png[/IMG]
[/URL]


if you want you can try the 396 driver released a couple days ago: [http://www.nvidia.com/download/driverResults.aspx/133859/en-us](http://www.nvidia.com/download/driverResults.aspx/133859/en-us) (found via [http://www.nvidia.com/Download/Find.aspx](http://www.nvidia.com/Download/Find.aspx) )
**i do not recommended this for new users, as this requires manual installation after kernel updates (at least last time i installed the like this)**

---

### Post by alexpirine on 2018-05-15
The thing is that I feel like I'm wasting a lot of time trying to solve this problem.

Time not being available: I prefer to just buy a new card that just works.

What's my best bet? Under $100?

Thanks!

---

### Post by jgw on 2018-05-16
I just installed:
gigabyte motherboard ga-f2a78m-hd2
amd apu  a8-7650K w/radeon r7 graphics  fm2+

isplay     (sudo lshw -c video)            
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]

Works fine and the built in video did the trick.  It automatically installed the radeon driver.  I have a resolution  3820x2160

The trick is setting it all up and I have tried everything to deal with the display - good luck!

---

