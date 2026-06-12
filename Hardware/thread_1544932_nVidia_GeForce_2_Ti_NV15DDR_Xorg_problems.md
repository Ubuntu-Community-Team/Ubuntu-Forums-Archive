---
title: "nVidia GeForce 2 Ti NV15DDR Xorg problems"
date: 2010-08-03
forum: Hardware
---

### Post by rossmounce on 2010-08-03
I'm running Peppermint OS (32-bit) on an old computer [details further below].

**The problem**: Xorg takes up 50-100% of my CPU all the time. This is very annoying. I think it's something to do with my graphics card driver (perhaps?).

Any ideas how I could fix this or further illuminate what's going on?

Thanks ;)

output from *top*:

"
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                              
  701 root      20   0 56712  21m 8880 R 50.1  2.1  93:22.47 Xorg                                                 
 4433 ross      20   0 53584  11m 8828 S 11.2  1.1   0:09.38 lxterminal                                           
 5404 ross      20   0 51168  17m 7320 S 10.6  1.7   7:55.08 lxtask                                               
 4576 ross      20   0  173m  43m  22m S  3.6  4.4   2:16.85 prism-bin                                            
 2136 ross      20   0  284m 103m  29m S  2.3 10.3  18:16.71 firefox-bin                                          
 3722 ross      20   0  250m  54m  27m S  1.3  5.4   2:39.24 prism-bin                                            
 1076 ross      20   0 84576  17m  12m S  0.7  1.7   3:22.90 lxpanel                                              
 6010 ross      20   0  2536 1160  888 R  0.7  0.1   0:00.37 top                                                  
"

output from *inxi -F*:

System:    Host ross-lab Kernel 2.6.32-22-generic i686 (32 bit) Distro Peppermint
CPU:       Single core AMD Athlon (UP) cache 256 KB flags (sse) bmips 2289.97 clocked at 1144.986 MHz 
Graphics:  Card nVidia NV15DDR [GeForce2 Ti] X.Org 1.7.6 Res: 1920x1080@60.0hz 
           GLX Renderer Software Rasterizer GLX Version 2.1 Mesa 7.7.1 Direct Rendering Yes
Audio:     Card-1 Creative Labs SB Live! EMU10k1 driver EMU10K1_Audigy at port d000 
           Card-2 Silicon Integrated Systems [SiS] AC'97 Sound Controllerdriver Intel ICH at ports d800 d400 
           Sound: Advanced Linux Sound Architecture Version 1.0.21
Network:   Card Realtek RTL-8139/8139C/8139C+ driver 8139too v: 0.9.28 at port cc00 
Disks:     HDD Total Size: 250.1GB (7.3% used) 1: /dev/sda Hitachi HCS72502 250.1GB 
Partition: ID:/ size: 23G used: 2.2G (10%) fs: ext4 ID:/home size: 205G used: 15G (8%) fs: ext4 
           ID:swap-1 size: 2.05GB used: 0.00GB (0%) fs: swap 
Info:      Processes 126 Uptime 3:55 Memory 415.2/1002.4MB Client Shell inxi 1.3.2

---

### Post by rollin on 2010-08-03
Hi and welcome but surely you would be better off asking it at the Peppermint Forum? [http://peppermintos.net/index.php](http://peppermintos.net/index.php)

---

### Post by rossmounce on 2010-08-03
Already did: [http://peppermintos.net/viewtopic.php?f=8&t=1211](http://peppermintos.net/viewtopic.php?f=8&t=1211)

[That thread is locked now, I'd like a little more explanation than just that my card "is not officially supported" if that's do-able?] 

The thing is, it's not a Peppermint specific problem. I had exactly the same problem when I had Ubuntu (Lucid) installed (only worse, because the rest of the system used more resources, switching to Peppermint has alleviated it somewhat but it's still a problem...).

Would changing graphics driver help? I've read there's 'nv' and 'nouveau' drivers possibly available(?) however i'm fairly novice at using linux so I don't even know which driver I'm using atm tbh...

---

### Post by rollin on 2010-08-03
Well I had a quick look at the linked post. The Mod did mention the threadjacking and to open another post if your issue is not solved. Unfortunately as I am not familiar with Peppermint I'll be honest and say I can't think of a quick solution. I'd still recommend you follow the Mod advice and create a linked post at the Peppermint Forum. Other than that you could try starting with [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia). This should help you to install a restricted driver for the card and see if that helps. Short of the advice above you could wait to see if someone here is running an Ubuntu dual boot with Peppermint who can help more. Good luck either way!

---

### Post by rossmounce on 2010-08-03
Thanks for the wiki link. I'll have a go with that.

---

