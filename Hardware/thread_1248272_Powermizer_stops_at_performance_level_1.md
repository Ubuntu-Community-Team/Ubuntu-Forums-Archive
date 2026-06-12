---
title: "Powermizer stops at performance level 1"
date: 2009-08-24
forum: Hardware
---

### Post by Appiah on 2009-08-24
Hello

Running Ubuntu 9.04 with 
* nvidia-glx-180 180.44-0ubuntu1 
* nVidia Corporation GeForce 9300M GS
* Linux 2.6.28-15-generic Ubuntu SMP x86_64 GNU/Linux


As you can see on the picture linked. Powermizer runs of maximum performance , performance level 1 but there is level 2 and 3 to go...
[http://godmelon.se/dump/powermizer.jpg](http://godmelon.se/dump/powermizer.jpg)

I never once seen it go over level 1.
Performance mode do however change from desktop to Maximum Performance once i launch a game or similar.

I tried putting this in my xorg.conf 

```
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"   
    Option        "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
    Option         "Coolbits" "1"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
```

Now it's always on maximum but never goes above level 1.

Output from : nvidia-settings -q GPUPerfModes -t
```
/perf=0, nvclock=169, memclock=100 ; perf=1, nvclock=275, memclock=250 ; perf=2,
nvclock=500, memclock=400 ; perf=3, nvclock=580, memclock=400

```

Cant find any warnings or error in Xorg.0.log that can relate to this problem. Any ideas?

---

### Post by Clamport on 2011-04-24
> **Appiah said:**
> Hello

Running Ubuntu 9.04 with 
* nvidia-glx-180 180.44-0ubuntu1 
* nVidia Corporation GeForce 9300M GS
* Linux 2.6.28-15-generic Ubuntu SMP x86_64 GNU/Linux


As you can see on the picture linked. Powermizer runs of maximum performance , performance level 1 but there is level 2 and 3 to go...
[http://godmelon.se/dump/powermizer.jpg](http://godmelon.se/dump/powermizer.jpg)

I never once seen it go over level 1.
Performance mode do however change from desktop to Maximum Performance once i launch a game or similar.

I tried putting this in my xorg.conf 

```
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"   
    Option        "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
    Option         "Coolbits" "1"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
```Now it's always on maximum but never goes above level 1.

Output from : nvidia-settings -q GPUPerfModes -t
```
/perf=0, nvclock=169, memclock=100 ; perf=1, nvclock=275, memclock=250 ; perf=2,
nvclock=500, memclock=400 ; perf=3, nvclock=580, memclock=400

```Cant find any warnings or error in Xorg.0.log that can relate to this problem. Any ideas?

I know that this thread is dead and rotting in the ground by now, but can you boot with debug kernel parameter, and output your dmesg and xorg.0.logs, as well as your hardware config?

I have 3 laptops, 2 Alienwares and an Asus. Alienware A has a 620M and gets full GPU performance, Alienware B has a 740QM and only gets to power state 2. When I switch the processors, GPU performance follows the 620M. Now I just need to get enough data to find a software fix.

Regards,
Clamport

---

### Post by Appiah on 2011-04-25
Hello

This problem went away with a new version of nvidia-drivers.
At that time the new drivers were in PPA and 9.10.

Are you expericing this problem on recent versions of ubuntu? 
10.04 (and up?)

---

### Post by Clamport on 2011-04-25
Yes, this bug is still a problem in the current distributions.

---

### Post by tkod on 2011-04-26
I'm not completely sure but I think this is a problem for me too. I have a laptop HP 8540W with NVIDIA Quadro FX880M, core i7-720qm.

Output of nvidia-settings -q GPUPerfModes -t:
perf=0, nvclock=135, memclock=135, processorclock=270 ; perf=1, nvclock=405,
memclock=324, processorclock=810 ; perf=2, nvclock=550, memclock=790,
processorclock=1210

Switching between perf0 and perf1 is ok, compiz runs smooth, but as much as the nvidia-applet shows it never goes to perf2 mode.
I have done benchmarks with Unigine Heaven and Sanctuary getting 13 and 33 fps in Linux while with the same settings in Win7 I get respectively 24 and 52 fps (both with opengl rendering exact same settings) which was the first thing that made me think something is not working fine.

I have tried all the perflevelsrc hacks and with trial and error managed to lock it in perf0 and perf1 modes and other different combinations for ac and battery power but never to maximum performance although I ran glxgears for each setup and got around 5-6 different results ranging from 650 to 4000 fps.

I also tested WoW in wine with opengl rendering and it gets solid 30fps on max settings and 1600x900 resolution which is quite good but in Win7 I get around 40-45fps for the same settings (although this may be completely due to the game).

Most of all while running the Unigine Benchmarks my graphics card runs much hotter on Win7 than on Ubuntu which I'm quite sure means that I'm not running on max performance on Ubuntu.

Using Ubuntu 10.10 x64, 2.6.35-28-generic
nvidia drivers downloaded - tried with both development driver 260.19.26 and normal driver 270.41.06

Please if someone can help ask me for all the information you need. I'm really upset because I have been using an old laptop with ATI X1300 for a long time before i got this one and it had no accelerated drivers for linux whatsoever from a certain x version, and now I'm getting practically the same crap from nvidia...

---

