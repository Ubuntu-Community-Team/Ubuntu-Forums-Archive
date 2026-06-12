---
title: "Compaq Presario M2000 is hopeless"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by luopio on 2005-08-22
[font=Lucida Sans Unicode][size=2]A friend just bought a presario M2000 ([/size][/font][font=Arial Narrow][size=1][font=Lucida Sans Unicode][size=2]Compaq Presario M2207AP (ED114PA)[/size][/font][font=Lucida Sans Unicode][size=2]) and wanted me to install linux on it. Being a Gentoo man myself, I decided Ubuntu would suit her better (easier, better localization, etc.). I tried Hoary and then after serious problems I tried Debian 3.1 (and of course the same problems persisted :???:). 

I'm installed kernel 2.6.13-rc6-mm1 and even it has no hardware support whatsoever for this crappy excuse for a laptop. I did however manage to get harddisk dma-transfers to work (one problem of twenty solved).. 

**lspci **gives me this: 
[font=Lucida Console][size=1]~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:09.0 CardBus bridge: Texas Instruments: Unknown device 8031
[/size][/font]
Seems quite hopeless doesn't it? Does anyone have any ideas on what to do, or where to report this "unsupportness of the kernel"? Any help would be appreciated.. the only option I currently have is to install windows :( 
[/size][/font][/size][/font]

---

### Post by tmilam on 2005-08-22
Nah not hopeless :) You need to run
```

update-pciids & update-usbids
```

Then you'll have a better of idea of what ya need. (modules)

---

### Post by tmilam on 2005-08-22
Oh yeah how did you get DMA working?

Just a wild guess, but you'll probably need the module atiixp

---

### Post by luopio on 2005-08-22
:shock:  Magic! Ok. At least now I have: 
[FONT=Lucida Console][SIZE=1]$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
[/SIZE][/FONT]

And good guess about the dma. I got it working with atiixp compiled in, but I have to use kernel 2.6.13, because earlier ones don't work. I also got X.org to work by using the vesa-driver for the videocard (although it should be supported by the ati-driver..). 

Now I have one major problems: 
1) the computer freezes every few ten seconds or so, if there is no activity (with mouse or keyboard). I have to press a button or tap the touchpad.

[EDIT] ok. now I'm quite sure the problem is related to the internal clock problem I have. The internal clock of the kernel advances a lot faster than the hwclock.. I'm trying to find a solution. any help appreciated! :) [/EDIT]

---

### Post by tmilam on 2005-08-22
> I have to use kernel 2.6.13, because earlier ones don't work.

How did you do this? Did you get vanilla sources and build the kernel yourself? Did you need an initrd? I've built alot of kernels but never on a distro that used initrds....
> 
the computer freezes every few ten seconds or so, if there is no activity (with mouse or keyboard). I have to press a button or tap the touchpad.

Weird! Maybe this is a power management issue? You can turn off powernowd if you have a turion because it doesn't do any good anyways. Supposedly 'power management is known not to be supported' on turions.  :roll: 

This pretty much means no speed stepping. 

I'd really like to hear how you built that new kernel!  :)

---

### Post by tmilam on 2005-08-22
I see you edited your post in regards to the hwclock. I'm having the same problem but haven't bothered fixing it yet. So far for me it's only caused me clock to be wrong. There is a setting you can use on the kernel line to fix it, so I've heard....I looked back at your lspci and our hardware is *remarkably* similar. All of my stuff is exactly the same!

---

### Post by tmilam on 2005-08-22
w00t found the fix for the clock problem! To your kernel line in grub.conf append
```

no_timer_check=0
```

I think I heard this isn't supported in kernel versions earlier than 2.6.12 though. Not sure if that's right.

---

### Post by Ptero-4 on 2005-08-22
[QUOTE=tmilam]w00t found the fix for the clock problem! To your kernel line in grub.conf append
```

no_timer_check=0
```

I think I heard this isn't supported in kernel versions earlier than 2.6.12 though. Not sure if that's right.[/QUOTE]
 Tmilam. It's gona work in his kernel since he said he's using 2.6.13 (one revision later than the known to work kernel revision).

---

### Post by tmilam on 2005-08-22
I just built 2.6.12 vanilla sources from scratch and the no_timer_check=0 option in the kernel line isn't working!! Right now my clock says it's 2200, but it's actually 2013 

:(  ](*,)   :? 

But on a more positive note at least now I have ati drivers working :D

It's not much of an improvement. glxgears gives me 350fps. Not much for gaming...

---

### Post by luopio on 2005-08-23
[QUOTE=tmilam]How did you do this? Did you get vanilla sources and build the kernel yourself? Did you need an initrd? I've built alot of kernels but never on a distro that used initrds....
[/QUOTE]

Yep. I got the vanilla sources and patched them to 2.6.13-rc6-mm1. Then I compiled them the old fashioned way: sudo make && sudo make modules_install && sudo make install. I tried *make-kpgk kernel_image*, but it didn't work (complained about "kernel_version.mk" file, which doesn't even exist). 

On my Gentoo laptop I've never used initrd, but on Debian and Ubuntu it seems that I must. I just use mkinitrd -o initrd.img 2.6.13-rc6-mm1 and edit the boot parameters.

[QUOTE=tmilam]Weird! Maybe this is a power management issue? You can turn off powernowd if you have a turion because it doesn't do any good anyways. Supposedly 'power management is known not to be supported' on turions.  :roll: 
[/QUOTE]

I turned powernowd off, but it didn't help.. I'll try no_timer_check  once the kernel finishes compiling...

And the system clock is not "drifting" - its really racing. See here(hwclock tells the real difference in time):
[SIZE=1]veera@kirottukannettava:~$ hwclock
ti 23. elokuuta 2005 09:36:00  -2.351557 sekuntia
veera@kirottukannettava:~$ date
ti elokuun 23. 09:35:15 EEST 2005
veera@kirottukannettava:~$ hwclock
ti 23. elokuuta 2005 09:50:14  -0.420083 sekuntia
veera@kirottukannettava:~$ date
ti elokuun 23. 09:59:34 EEST 2005
[/SIZE]

This affects - I believe - my keyboard repeat rate (which is insane currently) and (for  example) the speed of animations (the "loading" mouse cursor, these smilies in this replybox..).

I'll get back to you once I get this kernel compiled and tested..

---

### Post by luopio on 2005-08-23
Ok! it works enough good for me.  \\:D/ 

Booting the new kernel from which I ripped out **all ACPI and CPU freq.scaling support** and using **no_timer_check=0** as a boot option, the laptop works.. everything is still running at doublespeed, but that doesn't matter so much (at least to me.. not my laptop anyway).

My tactic now is to wait for new versions of the kernel and then perhaps - someday - this laptop will have working acpi and cpu-freq-scaling support.

And thanks for all the help (especially you tmilam)!

---

