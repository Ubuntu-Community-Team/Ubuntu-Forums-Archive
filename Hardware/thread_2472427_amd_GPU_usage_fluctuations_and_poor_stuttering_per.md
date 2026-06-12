---
title: "amd GPU usage fluctuations and poor stuttering performence in games (20.04)"
date: 2022-02-26
forum: Hardware
---

### Post by mattealex on 2022-02-26
**&#8203;**[Corectrl GPU stats after playing BL2 for a couple of minutes][1]


As you can see in the screenshot, my GPU (amd radeon rx 5500xt) is having trouble keeping a stable frequency and usage percentage. The activity goes from 5%-95% every couple of seconds for some reason and the frequency is spiking similarly as well. The Voltage and power seem to be fluctuating also but not as aggressively, (maybe those are atleast fine?). BIOS is on almost default settings, (maybe some change). 


The main issue is that in basically all the games I have tried has either microstuttering, stuttering, lag spikes or other performence issues. Borderlands 2 specifically has stuttering and low fps on steam (no compatibility tool).


[System monitor showing CPU core usages and system memory usage from the same time frame][2]


The CPU cores are pretty equal but staying at 35%-60% all the time. The memory doesn't seem very relevant to look at imo. AND also Some of the text could be in Swedish but I think you can understand the context anyways hopefully!


[Corectrl showing the CPU frequency with the same load][3]


It can be difficult to read the CPU and GPU graphs from Corectrl because there is no grid or numbers. But I looked at the live update of the value and it was a pretty wide range on the CPU graph as well. The bottom of the graph is actually 0 mHz.


[Image displaying scale of graph][4]


In the image, the current frequency is at 803 mHz almost at the bottom for reference.


[Borderlands 2 video settings][5]


You can't see Vsync or framrate but, Vsync is off and framrate is set to unlimited. I am running the game via steam without proton.


System details from Hardinfo report:


**Version**
Kernel    Linux 5.13.0-30-generic (x86_64)
Version    #33~20.04.1-Ubuntu SMP Mon Feb 7 14:25:10 UTC 2022
C Library    GNU C Library / (Ubuntu GLIBC 2.31-0ubuntu9.2) 2.31
Distribution    Ubuntu 20.04.4 LTS


**Computer**
Processor    Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz
Memory    8067MB (3540MB used)
Machine Type    Desktop


**SCSI Disks**
ATA ST1000DX002-2DV1    
ATA HFS128G3BMND-321


**Display**
Resolution    1920x1080 pixels
Vendor    The X.Org Foundation
Version    1.20.13
Current Display Name    :0


**Monitors**
Monitor 0    1920x1080 pixels


**OpenGL**
Vendor    AMD
Renderer    AMD Radeon RX 5500 XT (navi14, LLVM 13.0.1, DRM 3.41, 5.13.0-30-generic)
Version    4.6 (Compatibility Profile) Mesa 22.1.0-devel (git-a5fa7e0 2022-02-24 focal-oibaf-ppa)
Direct Rendering    Yes


It is worth adding that I have good temps when gaming (cpu: 50-60 C, gpu: 50-60 C). And I also have a coolermaster 500W 80+ Bronze PSU. As wifi I use Neatgear A6210 AC1200 USB with dongle. On the CPU I just have the stock intel cooler (no temp issues).


I have tried Borderlands with proton 7.0-1


Minecraft has similar problems and the graphs from Corectrl and system monitor shows that. (I thought it wasn't necessary to do screenshots again). In the game the trouble is especially chunk loading, where CPU usage goes to 100% and GPU usage drops. Which to me looked like a temporary CPU bound bottleneck, but I am not sure. I am aware that my hardware has a slight bottleneck like any system. However I have not experienced these issues before moving over to ubuntu from windows about half a year ago. It is worth to mention that I have installed ubuntu 20.04 via live USB and also reinstalled it just a few days ago because of another unrelated issue.


Minecraft also has big framedrops which I can see with optifine on the 1.8.1 version. With optimized settings I can go from around 60-80 fps average (with drops) to 200-500. Installing openjdk-17-jre helps with chunk loading. The chunk loading still affects framerate but goes a lot faster and has fewer OpenGL errors.


I installed minecraft via official minecraft.net deb-package and optifine via optifine.net.


I tried with all kinds of different settings both changing vanilla and optifine settings but nothing seems to affect this issue. Fullscreen/windowed, Vsync on/off, high/low graphics, different minecraft versions etc. This is probably the same as with borderlands as I can see when gpu activity drops to sub 20% at the same time as the framedrop happens.


Stuttering also happens in:
Warthunder (steam/steam proton)
world of tanks blitz (steam/steam proton)
eurotruck sim 2 (steam/steam proton)


I just cannot figure out what this is. To me this could be anything! At first I thought it was a driver issue but I have tried not messing with drivers (default) and also amdgpu-pro which apparently is not great to use. I do not think this is a hardware problem since this didn't occur when running windows. (The machine hasn't changed since).


It really feels like this has a simple solution I am not seeing.
If you need more info just ask because I probably forgot something here, Thanks for help :)


**Edit:**
I found inhardinfo that there was a CPU powersave gouvernor, and thought that might be limitting performence. I am focusing on CPU performence now because when the pc is stressed, CPU usage goes up to max and gpu usage is unstable or low. Managed to turn off the powersave on all cores with this command:


    echo performance | sudo tee /sys/devices/system/cpu/cpu[0-9]*/cpufreq/scaling_governor


output:


    performence


checked with:


    cat /sys/devices/system/cpu/cpu[0-9]*/cpufreq/scaling_governor


and got:


    powersave
    powersave
    powersave
    powersave


then I tried minecraft but the problem was still there, so I wanted to stress test the CPU and see if there is a difference. It turns out there isn't. Both results with powersave and performence are about this bad:


CPU Blowfish
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **2,11**


CPU CryptoHash
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **719,74**


CPU Fibonacci
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **0,51**


CPU N-Queens
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **6,65**


CPU Zlib
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **0,92**


FPU FFT
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **0,78**


FPU Raytracing
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **1,98**


GPU Drawing
Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz    4x 3600,00 MHz    **7255,17**


For reference:
core 2 duo got multiple times better results on some of the tests. But the GPU Drawing and CPU crypto hash are better for some reason.


  [1]: [https://i.stack.imgur.com/s8HK6.png](https://i.stack.imgur.com/s8HK6.png)
  [2]: [https://i.stack.imgur.com/M6jlp.png](https://i.stack.imgur.com/M6jlp.png)
  [3]: [https://i.stack.imgur.com/M7LK7.png](https://i.stack.imgur.com/M7LK7.png)
  [4]: [https://i.stack.imgur.com/0xvT1.png](https://i.stack.imgur.com/0xvT1.png)
  [5]: [https://i.stack.imgur.com/QwM8M.jpg](https://i.stack.imgur.com/QwM8M.jpg)

---

