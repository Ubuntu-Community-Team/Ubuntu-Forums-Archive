---
title: "firefox flash problem....."
date: 2008-08-12
forum: General Help
---

### Post by Kaneda187 on 2008-08-12
the problem is when I'm on youtube or any similar sites flicking through vids my firefox suddenly closes with no warning or anything just ............poof....gone! 

any ideas?

I'm using adobe flash player as far as I know. I dont know what version though. 

HELP ITS REALLY BUGGIN ME! 

Thanks in advance.

---

### Post by Crafty Kisses on 2008-08-12
It could be a resource issue, post the following ouput
```
top
```
Also alternatively you can uninstall and try "Gnash".

---

### Post by Kaneda187 on 2008-08-12
I hate gnash!! not going ther! 
heres the info from top

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6426 kaneda    20   0  226m  74m  26m S   29  3.7   1:37.90 firefox            
 5503 root      20   0  377m  86m  19m S   21  4.3   1:47.13 Xorg               
 5913 kaneda    20   0 22984  15m 5892 S    1  0.8   0:10.60 compiz.real        
 7493 kaneda    20   0 74548  19m  10m S    1  1.0   0:00.40 gnome-terminal     
 5736 kaneda    20   0  7260 4316 1904 S    1  0.2   0:00.68 gconfd-2           
 6186 kaneda    20   0 19976  10m 6432 S    1  0.5   0:29.08 kiba-dock          
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.36 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelp

---

### Post by Kaneda187 on 2008-08-12
thats when im playin a vid on youtube too in case your wondering,

any ideas? thanks

---

### Post by Crafty Kisses on 2008-08-12
> **Kaneda187 said:**
> thats when im playin a vid on youtube too in case your wondering,

any ideas? thanks

Is it only on YouTube or any flash site?

---

### Post by Kaneda187 on 2008-08-13
sorry took me a while to get back to ya.....nope not just youtube any flash! got any ideas? do you think its a problem with firefox or adobe or something else?

THANKS GUYS!!!:)

---

### Post by todak on 2008-08-13
Try removing the file **libflashsupport**. I did and no more crashes on flash sites w/FF3.

---

### Post by Kaneda187 on 2008-08-13
wher is the file located?

---

### Post by todak on 2008-08-13
```
sudo apt-get remove libflashsupport
```

---

### Post by mb_webguy on 2008-08-13
The version of the Flash plugin in the Hardy repositories has compatibility problems with PulseAudio, which are *supposed* to be resolved with the libflashsupport package.  If you *don't* have it installed, do so and see if it helps.  (And as the others have said, if it *is* installed, then you can *uninstall* it and see if that helps, but I doubt it will.)

Alternatively, you can install the newest version of the Adobe Flash plugin (which is very stable), which is in the Intrepid repository.  You can download it [here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree").

---

### Post by todak on 2008-08-13
I ran into Firefox crashing on youtube, etc. with  libflashsupport and pulse audio. In my case, it was remedied by removal of the libflashsupport library and no other changes. I suppose it may behave differently depending on hardware configurations from computer to computer.;)

---

### Post by Kaneda187 on 2008-08-30
I think that worked dude thanks!!

---

### Post by NightCrawler03X on 2008-08-30
Man, since Ubuntu 8.04 and the introduction of PulseAudio I've seen nothing but problems on my system. I've seen countless people report problems on this forum too. Even before PulseAudio, people would still have audio problems here and there (ALSA has it's share of problems, believe it or not).

I would actually advise that the next release of ubuntu has neither ALSA nor PulseAudio, instead using OSS4 and ESD. On my system, I've replaced ALSA and PulseAudio with OSS4 and ESD. I no longer have *any* sound-related problems on my system.

If anyone here is interested in OSS4, just check this link:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

