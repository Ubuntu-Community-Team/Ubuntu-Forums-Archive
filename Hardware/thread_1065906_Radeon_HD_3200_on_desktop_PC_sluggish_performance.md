---
title: "Radeon HD 3200 on desktop PC sluggish performance"
date: 2009-02-10
forum: Hardware
---

### Post by RWIndiana on 2009-02-10
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
        Subsystem: Giga-byte Technology Device d000                            
        Flags: bus master, fast devsel, latency 0, IRQ 18                      
        Memory at d0000000 (32-bit, prefetchable) [size=256M]                  
        I/O ports at ee00 [size=256]                                           
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]               
        Memory at fde00000 (32-bit, non-prefetchable) [size=1M]                
        Capabilities: [50] Power Management version 3                          
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Kernel driver in use: fglrx_pci                                                
        Kernel modules: fglrx  
```

^ That is the output of lspci -v
My resolution is 1440x900 (60hz). My problem is that it performs quite poorly, so much so that the graphics seem to be the bottleneck of the entire system! Even with compositing disabled (by the way I am running Kubuntu 8.10 with KDE 4.2, which works excellently on my laptop with a GMA 945 at the same resolution), redrawing is a bit jerky and the system feels sluggish. Maybe it's a combination of problems, but I do know the graphics at least is not working very well. Any ideas how to improve the graphics and/or the entire system's performance? I have a AMD64 X2 5000+ with 1 gig of ram.

---

### Post by Yellow Pasque on 2009-02-10
I've experienced the same issues with fglrx (on Ubuntu and other distros). It's just not fast with 2D operations. Unfortunately, the open-source alternatives aren't end-user ready when it comes to hardware acceleration for the RS780 (though they are under rapid development now that they have the documentation).

---

