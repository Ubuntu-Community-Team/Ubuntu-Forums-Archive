---
title: "Lost sound after auto update"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by thoffland on 2007-07-07
I have a Thinkpad T30, and today the auto update icon popped up, and installed 3 updates. 2 were for the update manager (i think) but I dont recall what the 3rd was for. Now I have no sound, and have gone through the comprehensive sound thread without luck. I have the drivers installed and it's recognizing my sound card. Also, alsamixer is not muted on any channel and the volume is up on my laptop. I've also added the name of the driver to my /etc/modules file without any luck. 

Any ideas??? 


aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 1: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM ThinkPad T30
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
```


sudo modprobe snd-intel8x0
```
snd-intel8x0   snd-intel8x0m  
```

---

