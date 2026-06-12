---
title: "Hp Pavilion dv6-1220so - Problems"
date: 2009-08-16
forum: Hardware
---

### Post by Quinz on 2009-08-16
Hi, I've been searching around on google and tried my luck on IRC, but still I'm not any closer to a solution for my problems:

1) No sound
2) Not able to use the built-in webcam with amsn

As for the first i have updated the alsa sound driver, with seemingly no effect at all.
```
quinz@Laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Aug 17 2009 for kernel 2.6.28-11-generic (SMP).
quinz@Laptop:~$

```lshw: Multimedia
```
        *-multimedia                                                                                      
             description: Audio device                                                                    
             product: 82801I (ICH9 Family) HD Audio Controller                                            
             vendor: Intel Corporation                                                                    
             physical id: 1b                                                                              
             bus info: pci@0000:00:1b.0                                                                   
             version: 03                                                                                  
             width: 64 bits                                                                               
             clock: 33MHz                                                                                 
             capabilities: pm msi pciexpress bus_master cap_list                                          
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```As for my second problem, anyone know why Amsn cant connect with my webcam? Tried "Cheese" and it worked perfectly.

Thanks for any help provided! :)

---

### Post by BigCityCat on 2009-08-16
I dont know much but there are two things I can tell you. 1st click on you speaker icon, click on mixer and turn pcm all the way up. If that doesn't work go here.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Quinz on 2009-08-16
Still nothing, going to check your link out. Cheers :)

edit: Still no sound whatsoever :<

Anyone got some ideas?

---

### Post by BigCityCat on 2009-08-16
Try this one.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Quinz on 2009-08-16
Ye, just found it :) working on it now

Edit: Well, it's strange since as far as i can tell the soundcard is there, and with drivers installed - or?
```
quinz@Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 3628                                   
        Flags: bus master, fast devsel, latency 0, IRQ 22                                
        Memory at da100000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel
```

[SIZE=2]**alsamixer **is not muted either :<[/SIZE]

---

### Post by Ozzee on 2009-09-21
I was just wondering if you ever got the sound to work? 

I have the same problem.

Thanks :)

---

