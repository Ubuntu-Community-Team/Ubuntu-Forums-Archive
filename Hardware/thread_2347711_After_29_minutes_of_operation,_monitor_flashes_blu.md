---
title: "After 29 minutes of operation, monitor flashes blue, yellow, pink, green, etc"
date: 2016-12-27
forum: Hardware
---

### Post by bwindsor22 on 2016-12-27
After 29 minutes, the monitor does this: [https://drive.google.com/file/d/0Bxb68gC3mxwiUlRUUmtjZkhlVlk/view](https://drive.google.com/file/d/0Bxb68gC3mxwiUlRUUmtjZkhlVlk/view) Could someone advise if this is a hardware issue?

Some debugging information:
[COLOR=#000000][FONT=Arial]lspci | grep VGA:  the graphics card is as follows: 00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Sudo apt-get update, sudo apt-get upgrade: Ubuntu is up to date[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Xrandr: the frame rate and monitor resolution matches the minimum specified by the monitor manual (1920x1080 [/FONT][/COLOR][COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]60.00)
Xorg Config output: [https://docs.google.com/document/d/16sEJcHbDMMgQkMaN00Z6sCD48uT3uELUNBLPy28WOzc/edit?usp=sharing](https://docs.google.com/document/d/16sEJcHbDMMgQkMaN00Z6sCD48uT3uELUNBLPy28WOzc/edit?usp=sharing) 

Related threads: 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/444363](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/444363)  -- Nvidia driver issue (?) (mine is Intel)
[http://forum.notebookreview.com/threads/screen-now-flashing-red-green-blue-white-black.556517/](http://forum.notebookreview.com/threads/screen-now-flashing-red-green-blue-white-black.556517/)  -- Graphics card issue on Windows[/FONT][/COLOR]

---

### Post by ajgreeny on 2016-12-28
Always exactly 29 minutes or is that an average time?

It certainly looks like a graphic card problem to me or possibly the transfer of signal to monitor; what cable are you using HDMI, DVI-x or good old VGA?

---

### Post by him610 on 2016-12-29
> After 29 minutes,  the monitor does...
If this occurs consistently after 29 minutes then the chances are that it is hardware related, and it is probably heat related. Could possibly be graphics card/chip or monitor. Are your cooling fans operating as they should? 
If you have a spare monitor, try swapping it with one you have currently installed. 
If you are using a discrete graphics card then it too is replaceable. 
If you have a gpu that is combined with your cpu, then you might try cleaning the mating surfaces of the heatsink/cpu and reapplying heatsink compound.

---

### Post by Yellow Pasque on 2016-12-30
So is the screensaver or something else set to run after 30 mins? DPMS?
```
xset -q
```

---

