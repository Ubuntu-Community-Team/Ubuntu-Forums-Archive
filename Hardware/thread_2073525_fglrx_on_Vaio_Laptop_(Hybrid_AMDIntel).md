---
title: "fglrx on Vaio Laptop (Hybrid AMD/Intel)"
date: 2012-10-19
forum: Hardware
---

### Post by amiba on 2012-10-19
I'm having problems using the fglrx drivers in this laptop in the latest ubuntu. The computer has a hybrid graphic system (Radeon 6400/Intel). 

Using the ubuntu version of the drivers (9.000.3), xorg fails with a segmentation fault:

> [   566.695] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[   566.695] (EE) 
[   566.695] (EE) Backtrace:
[   566.740] (EE) 0: X (xorg_backtrace+0x36) [0x7fe464e34ac6]
[   566.740] (EE) 1: X (0x7fe464c8c000+0x1ac8f9) [0x7fe464e388f9]
[   566.740] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fe463fb2000+0xfcb0) [0x7fe463fc1cb0]
[   566.740] (EE) 3: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxPxPreInit+0xca) [0x7fe46140e98a]
[   566.740] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxPreInit+0x1f59) [0x7fe4613eb5e9]
[   566.740] (EE) 5: X (InitOutput+0xb02) [0x7fe464d23af2]
[   566.740] (EE) 6: X (0x7fe464c8c000+0x44386) [0x7fe464cd0386]
[   566.740] (EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fe462c3776d]
[   566.740] (EE) 8: X (0x7fe464c8c000+0x448ad) [0x7fe464cd08ad]
[   566.740] (EE) 
[   566.740] (EE) Segmentation fault at address 0x0
[   566.740] 


while if I try to use the amd drivers (9.000), it fails to load  in this step:
> fglrx_drv.so: undefined symbol: noXFree86DRIExtension"  

Does anybody also have this problem?

Thanks

---

### Post by amiba on 2012-10-22
No one else with this problem?

---

### Post by amiba on 2012-10-30
Turns out to be a problem in the intel driver. 

Solved with the solution in [this post]("http://ubuntuforums.org/showpost.php?p=12324761&postcount=503")

---

