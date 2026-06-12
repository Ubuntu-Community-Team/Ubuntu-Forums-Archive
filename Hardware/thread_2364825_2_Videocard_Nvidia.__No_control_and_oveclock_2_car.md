---
title: "2 Videocard Nvidia.  No control and oveclock 2 card. Cannot save param"
date: 2017-06-28
forum: Hardware
---

### Post by dj--alex on 2017-06-28
I requires overclocking control two videocards.
I tries use Nvidia coolbits "12"  but it allow change settings  only in GUI , 
this settings reset on every reboot , but i require set fan to 100%   

I really requires this settings, i cannot just go and buy two GTX 1060. it too expensive for me.
i have two GTX 780.  on work temperatuge goes 85 , and computer shutdown.

core clock must de downclocked offset -100 -200
fan speed must be 100% .
I don't know how to do it in console

Please anybody help me to how use nvidia-settings -a -q for change parameters??
 
and what i must do in X11/xorg.conf  to add section for control overclock parameter for 2RD card

I use manual 2012 vvvhttp://syslinux.ru/node/1338
```
user@PC1 ~ $ nvidia-settings -a -q nvclock 0
nvidia-settings: invalid option: "nvclock"

ERROR: Invalid commandline, please run `nvidia-settings --help` for usage
       information.

user@PC1 ~ $ nvidia-settings -a -q memclock 0
nvidia-settings: invalid option: "memclock"

ERROR: Invalid commandline, please run `nvidia-settings --help` for usage
       information.
```
use another manual
```

$ 
user@PC1 ~ $ nvidia-settings --assign [gpu:0]/GPU3DClockFreqs="625,516"


DEPRECATED: The attribute 'GPU3DClockFreqs' is no longer supported.

```


i can save it and run automatically with cron.  but how to do this??

Simpliest way is buy 3x14cm fans but it not best solution.

I hear i can use export 
but i don't know how ot correct run it and where i can place it
commands like this
export GPU_USE_SYNC_OBJECTS=1
export GPU_MAX_ALLOC_PERCENT=100


Ubuntu Mate 16.04.5 x64 , Mint 18.1 x64  Kernels 4.10.14 , Nvidia 381,  2x GTX780

---

### Post by CatKiller on 2017-06-28
nvidia-settings stores its settings in **~/.nvidia-settings-rc**. You can load the settings stored in this file with ```
nvidia-settings --load-config-only
``` You can have this command run when you log in by putting it in your ~/.xinitrc. **man nvidia-settings** will give you more information.

In addition to setting the speed manually like this, you probably ought to try to work out why the GPU fan isn't turning on automatically.

---

### Post by Autodave on 2017-06-28
What driver(s) are you using for the card and where did you get it from? I am assuming that there is a monitor ONLY connected to one card?

---

### Post by dj--alex on 2017-06-28
how add attributes to both videocard? 
and how correct set parameters? 
i must write any word about overclocking and get some luck or i somewhere in internet exist word list to full it file? 

i search but still don't understand
[https://devtalk.nvidia.com/default/topic/831612/losing-overclock-after-reboot-346-59/](https://devtalk.nvidia.com/default/topic/831612/losing-overclock-after-reboot-346-59/)

how to fan settings to 100% ?
i see this message early

user@PC1 ~ $ nvidia-settings -a '[fan:0]/GPUCurrentFanSpeed=100'


ERROR: The attribute 'GPUCurrentFanSpeed' specified in assignment
       '[fan:0]/GPUCurrentFanSpeed=100' cannot be assigned (it is a read-only
       attribute).


=====

of course only one monitor. 
Nvidia 382  get from official PPA

on internet i found answer on 2nd question - how to overclock both cards
```
a
Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"

    DefaultDepth    24

    Option         "AllowEmptyInitialConfiguration" "True"

    Option         "Coolbits" "12"

    Option         "ConnectedMonitor" "DFP-0"
    Option         "RegistryDwords" "PerfLevelSrc=0x2222"

    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

 

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AllowEmptyInitialConfiguration" "True"

    Option         "Coolbits" "12"
    Option         "ConnectedMonitor" "DFP-0"
    Option         "RegistryDwords" "PerfLevelSrc=0x2222"
    SubSection     "Display"
        Depth       24

    EndSubSection

EndSection


```

oh i found something interest about multicard and save overclock data .
[https://forum.bits.media/index.php?/topic/38879-nastroika-gtx-1060-pod-linux/](https://forum.bits.media/index.php?/topic/38879-nastroika-gtx-1060-pod-linux/)
read later.  today is exhausted

---

### Post by CatKiller on 2017-06-28
If you're able to set the settings how you want them in the NVidia GUI application, there's a button that will save the configuration to ~/.nvidia-settings-rc. Then you can load them back automatically with the command I gave you before.

It's also just a text file, so you can also tweak the settings before you load them, with the usual warnings about potentially doing something silly with the settings.

---

### Post by dj--alex on 2017-06-29
It's no work
no one saved in .nvidia-settings-rc
# /home/user/.nvidia-settings-rc  - don't have  FAN options.


i find nvidiux but nvidiux from PPA didn't saved any settings after reboot

[https://bitcointalk.org/index.php?topic=1854250.msg18742952#msg18742952](https://bitcointalk.org/index.php?topic=1854250.msg18742952#msg18742952) - 

nvidia-settings -a [gpu:0]/GPUFanControlState=1
nvidia-settings -a [fan:0]/GPUTargetFanSpeed=75

im just add to autoload commands to my videocards to rc.local

partial solved.

---

### Post by dj--alex on 2017-07-01
not get answer

Cannot overclock any GPU>0  

Screenshot 
[https://pp.userapi.com/c840225/v840225257/1033e/5v2hp7Fs-sI.jpg](https://pp.userapi.com/c840225/v840225257/1033e/5v2hp7Fs-sI.jpg)

---

