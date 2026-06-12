---
title: "Switchable Graphics: How?"
date: 2011-07-12
forum: Hardware
---

### Post by pavben on 2011-07-12
Hey guys,

I just got an HP dv7t laptop which has two graphics cards:
1. Intel integrated card for saving battery
2. AMD Radeon HD 6470M for performance video

I'm running Ubuntu 11.04 with standard open-source video drivers for both (no proprietary drivers).

I've been looking for a way to switch among the two graphics cards as is possible on Windows -- completely seamlessly (haven't tried, but so I hear).

I'm hearing that vga_switcheroo is what I should use, but it doesn't seem to work fully on this laptop -- perhaps I'm doing something wrong?

Here's what it looks like as soon as I boot up the laptop:
```

root@anivia:~# cat /sys/kernel/debug/vgaswitcheroo/switch 
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Pwr:0000:01:00.0
```

This tells me that both cards are powered on, and integrated graphics is currently outputting to the screen.

By echoing OFF into /sys/kernel/debug/vgaswitcheroo/switch, I was able to power off the Radeon card, changing the above from Pwr to Off.

I've also tried:

> root@anivia:~# echo DIS > /sys/kernel/debug/vgaswitcheroo/switch

which, in dmesg, produces:
> [ 2023.661209] vga_switcheroo: client 0 refused switch


and I've tried echoing DDIS, which produces:
> [ 2110.733505] vga_switcheroo: client 0 refused switch
[ 2110.733515] vga_switcheroo: setting delayed switch to client 1

Logging out and back in after this has no effect, although after a reboot, IGD and DIS switch places (DIS is first, IGD is second), although IGD is still selected as active (+)

The system is certainly usable like this, although I do have issues with hibernation and sleeping (freeze-ups), which went away when I somehow disabled the Radeon driver (temporarily).

What can you guys suggest?

Ideally, I want to have control over powering on/off the two cards and switching the active to whichever one.

If that is not possible, I'd like to make the Radeon card my primary (not settable in BIOS) and never use integrated.

If that is not possible, same as above but the other way around: use integrated and permanently disable the Radeon card.

Also, should I consider using proprietary drivers for the Radeon card?

Thanks in advance,
Pav

---

### Post by pavben on 2011-07-13
Bump with additional details:

Before radeon was loaded, I manually tried:

modprobe radeon modeset=1

The output was as follows:
```

[  160.848678] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  160.848680] [drm] No driver support for vblank timestamp query.
**[  160.848682] [drm] Initialized radeon 1.33.0 20080528 for 0000:01:00.0 on minor 1**
[  179.673796] [drm] Module unloaded
[  193.984058] [drm] radeon kernel modesetting enabled.
[  193.984074] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[  193.984105] radeon 0000:01:00.0: setting latency timer to 64
[  193.985019] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6760).
[  193.985064] [drm] register mmio base: 0xC6500000
[  193.985066] [drm] register mmio size: 131072
[  193.985067] vga_switcheroo: enabled
[  193.985190] radeon atpx: version is 1
[  194.589918] ATOM BIOS: HP/Flex
[  194.590314] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[  194.590322] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[  194.590341] mtrr: no more MTRRs available
[  194.590345] [drm] Detected VRAM RAM=1024M, BAR=256M
[  194.590350] [drm] RAM width 64bits DDR
[  194.590560] [TTM] Zone  kernel: Available graphics memory: 4070256 kiB.
[  194.590565] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[  194.590569] [TTM] Initializing pool allocator.
[  194.590603] [drm] radeon: 1024M of VRAM memory ready
[  194.590608] [drm] radeon: 512M of GTT memory ready.
[  194.590631] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  194.590635] [drm] Driver supports precise vblank timestamp query.
[  194.590713] radeon 0000:01:00.0: irq 54 for MSI/MSI-X
[  194.590724] radeon 0000:01:00.0: radeon: using MSI.
[  194.590807] [drm] radeon: irq initialized.
[  194.590813] [drm] GART: num cpu pages 131072, num gpu pages 131072
[  194.591735] [drm] Loading CAICOS Microcode
[  194.658149] radeon 0000:01:00.0: WB enabled
[  194.675168] [drm] ring test succeeded in 2 usecs
[  194.675472] [drm] radeon: ib pool ready.
[  194.675637] [drm] ib test succeeded in 0 usecs
[  194.676646] [drm] Radeon Display Connectors
[  194.676672] [drm] Internal thermal controller with fan control
[  194.678127] [drm] radeon: power management initialized
[  194.678860] No connectors reported connected with modes
[  194.678871] [drm] Cannot find any crtc or sizes - going 1024x768
[  194.681800] [drm] fb mappable at 0xA0141000
[  194.681804] [drm] vram apper at 0xA0000000
[  194.681808] [drm] size 3145728
[  194.681811] [drm] fb depth is 24
[  194.681815] [drm]    pitch is 4096
[  194.681965] fb1: radeondrmfb frame buffer device
**[  194.681975] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 1**


```

Note the two lines in bold. Two versions of the driver?

I've also tried loading radeon in recovery mode (without GUI) and echoing "DIS" to vga_switcheroo -- it froze.

Another time, from GUI, when I echoed "OFF" to switcheroo, it killed my video and froze the machine.

Seems there's little consistency in the behavior... should I try some updated driver from PPA?

---

### Post by ubik89 on 2011-10-24
I got the same problem with Lenovo G770. It has intel integrated and Radeon HD 6650M. Switching causes a system freeze.

---

### Post by tomek_wap on 2011-10-29
is that switching graphics critical?
 
i am planning to buy either g570, but i think i will go for g770. and i am not sure whether that swiching graphics will be usefull for me ...
 
thnx

---

### Post by aeronutt on 2011-10-29
> **tomek_wap said:**
> is that switching graphics critical?
 
i am planning to buy either g570, but i think i will go for g770. and i am not sure whether that swiching graphics will be usefull for me ...
 
thnx

Switchable means you can turn the discrete graphics off, which can save tons of battery power on a laptop. My battery life was nearly doubled when I disabled my ATI HD6630M.

FYI, I don't know anyone that has gotten switchable graphics to work on a laptop with Intel SandyBridge integrated graphics and an AMD HD GPU.

---

### Post by tomek_wap on 2011-11-28
> **ubik89 said:**
> I got the same problem with Lenovo G770. It has intel integrated and Radeon HD 6650M. Switching causes a system freeze.

How do you actually do the switch? 
With the "vga_switcheroo" ?

I am still newbie with this switching business, and I wonder how you check which card is actually in use.
When I do "sudo lshw", it lists both Intel and ATI cards.

---

### Post by ubik89 on 2011-12-17
Yes, with vga_switcheroo.

I just can use the intel card. When i switch to radeon it causes system freeze when restarting X11.

---

### Post by Mark Phelps on 2011-12-19
The fix doesn't enable switchable graphics, quite the opposite -- it disables it so you can have the video work.  Switchable graphics, at least, the way it was designed to work in Windows, does not work in Ubuntu.

---

### Post by tomek_wap on 2011-12-21
I guess the Intel graphics suits well in Linux, unless you're trying to do some gaming.

Thank you for clearing that up.

---

### Post by Gato303co on 2011-12-23
Hello,
I have an Inspiron 15R N5110 laptop, with graphics integrated: Intel Graphics HD3000 and dedicated video graphics chip: Nvidia GT525M.

I would like to know the code to disable the Intel Integrated Graphics, to be able to install and run the Nvidia Linux driver and work always with the nvidia graphics chip.

I can't install the nvidia propietary graphics since there is some kind of conflict with the integrated intel graphics, and in the Nvidia website, they say the nvidia linux driver won't work "if means to disable the integrated graphics in hardware are not available".

I will thank you for your help.

---

### Post by Gato303co on 2011-12-26
Hello again,

I wanted to comment that when I install the nVidia propietary drivers, using Jockey-gtk, and then I restart Xubuntu, the switcheroo is gone!  it doesn't appear again in the /sys/kernel/debug/ folder anymore.

Can someone tell me what happened there?
Is there a possibility to recover the switcheroo?  Since I looked for it on the Synaptic package manager but it's not there as an installable package, and I really don't know what to do,thanks

---

