---
title: "display resolution problem"
date: 2014-02-08
forum: Hardware
---

### Post by jgw on 2014-02-08
I just reinstalled ubuntu.  my display:
*-display               
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memor

I have energized all the drivers (3) as each didn't seem to do the trick.  I cannot seem to get past:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

When I try and change my resolution with the nvidia program I am told that cannot be done as my driver is too old.  I have tried all three nvidia drivers (they are all currently activated - which I can change) with exactly the same notice.  My problem is that everything was working fine, then my entire system crashed and would not boot.  I was well backed up so I decided to just reinstall.  Now nothing works.  Its a very strange thing, I think.

there doesn't seem to be an output vga1, etc.  When I check my settings it tells me I am dealing with a laptop.  This is a desktop with a 23" display.

So, how do I deal with the gamma size thing and how does one get an some kind of output, agp1, etc.  I am, obviously really missing something here.

Any help would be appreciated - thank you................

---

