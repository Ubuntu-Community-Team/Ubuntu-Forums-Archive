---
title: "Microphone works in general but NOT WITH SKYPE"
date: 2009-05-26
forum: Hardware
---

### Post by frojnd on 2009-05-26
Hello there. I've been trying to find out how to make this work but It seem that I just can't.

Problem occurs when I call sykpe test call. I was very confused while watching the volume control during trying to record myself with echo call. In the volume control -> recording, wathching the capture how it decreased itself as soon as I start to speak when the echo lady says now, was outstanding...

I tried to increase the bar but I couldn't it keep falling down, decrease. And this only happens with skype.

I have ubuntu 9.04, pulse audio is set in skype for all devices. I also tried to change to pulse in system -> preferences -> sound -> Sound capture. I've set to pulse and alsa but neither work.

BUT ONLY IN SKYPE!

I've installed from this page: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I've added repo deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free 

refreshed and install skype.


I'm out of ideas. Why microphone won't work in skype?
Anyone that fixed this kinda problem please replay.

Thanx.

---

### Post by frojnd on 2009-05-27
**BUMP**

Maybe you can help me out if I can give you more hardware specs:

Sound card: 
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Device 01bd                                                                   
        Flags: bus master, fast devsel, latency 0, IRQ 21                                             
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]                                      
        Capabilities: [50] Power Management version 2                                                 
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Count=1/1 Enable-               
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00                           
        Capabilities: [100] Virtual Channel <?>                                                       
        Capabilities: [130] Root Complex Link <?>                                                     
        Kernel driver in use: HDA Intel                                                               
        Kernel modules: snd-hda-intel      
```

---

### Post by Nordfjord on 2009-09-23
Sorry to bring this back up after so long, but I'm having the exact same problem. I think I have almost the same audio controller as well.

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Does anyone have a solution or advice?

---

### Post by mikewhatever on 2009-09-23
How about unchecking 'Allow skype to adjust mixer levels' in skype's sound settings? As described by the OP, the mic does work, but when skype tries using it, the volume goes down.

---

### Post by frojnd on 2009-11-04
Yep that last thing worked. Found on the skype forums. Where can I change to SOLVED?

Found.

---

