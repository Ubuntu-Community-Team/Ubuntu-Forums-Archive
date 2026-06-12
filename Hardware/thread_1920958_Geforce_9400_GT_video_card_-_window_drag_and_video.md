---
title: "Geforce 9400 GT video card - window drag and video tearing in 10.04"
date: 2012-02-05
forum: Hardware
---

### Post by gobr3800 on 2012-02-05
Hi everyone,

I have been struggling for days to do a clean install of my system. I keep running into the same problem - window and video tearing. I'm assuming it's a problem with my video card, so I've been focussing on that. I did have it working fine before (on 10.04). Even though I'm trying to do the clean install on 10.04, the tearing just persists.

Here's what I do to try and set things up:

- Install the video driver Ubuntu recommends (the current Nvidia driver), then reboot.
- Check the 'sync to vblank' option in the NVidia X Server Settings.
- Check the 'sync to vblank' option in Compiz Config Settings Manager.
- Uncheck 'detect refresh rate' in CCSM.

This is the process I followed when I originally installed Ubuntu on this machine and it stopped the tearing fine. But now it doesn't seem to.

I've also tried installing 11.04 (and also 8.04 and 9.10) - I get tearing on all distros, so it doesn't seem to make a difference. I'd prefer to use the LTS version (10.04).

Any ideas on how I can fix the tearing?

Thanks!

Pablo

---

### Post by desnaike on 2012-02-05
Hope this helps I have the same card and experienced tearing with the recommended nvidia driver I just went down to the driver that preceded the recommended driver it worked. Not sure the ubuntu version # 10.04/10.10. You can do this until u find a fix,I fixed it by installing 11.10.

---

### Post by gobr3800 on 2012-02-05
Thanks heaps for the response! How do you go down a driver? Is it just the other one that comes up when I open the Hardware Drivers app? What's the version number of the driver you're using? (Maybe if I can somehow install that version mine will work - any idea how to request it install a specific driver version?)

Also, just remembered - I tried 10.10 as well! No luck :(

---

### Post by aasdfasdfg on 2012-02-05
> **gobr3800 said:**
> Hi everyone,

I have been struggling for days to do a clean install of my system. I keep running into the same problem - window and video tearing. I'm assuming it's a problem with my video card, so I've been focussing on that. 

Can you post the relevant output of ```
lspci -v
```Find the section that starts with ```
VGA compatible controller
```For instance, here is my output:
```
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9806 (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 2ac7
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

```

---

### Post by gobr3800 on 2012-02-05
Here's the output (NB. This is a fresh install with software updates only, no hardware updates):

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8296
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	Expansion ROM at fe880000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

Thanks!

---

### Post by gobr3800 on 2012-02-06
@ Desnaike - you can see what NVIDIA Driver Version you're using in NVIDIA X Server Settings > X Server Information. If you could let me know what version you've got there, I could try and install that manually.

@ aasdfasdfg - I've now installed the current video drivers on my fresh system (System > Administration > Hardware Drivers > NVIDIA accelerated graphics driver (version current) [Recommended]). Here's the new output of lspci -v:

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8296
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fe880000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

Any one got an idea of what I could do to prevent the tearing? I'm considering buying a new video card. But I would much prefer to get my machine operating with my old video card like it was before. It's really strange to me that the same video card would work on 10.04 on install and the next fail like it is now.

Thanks!

---

