---
title: "Keyboard and sound problems with Ubuntu 10.04 on HP G62"
date: 2010-08-31
forum: Hardware
---

### Post by OBAFGKM on 2010-08-31
Hi,

I've just bought a HP G62-a35SS. After installing Ubuntu (10.04) I realized that basically, the Fn key does not work at all. I'm no able to change the brightness, the volume... even the wireless can't be enabled. Also, the labtop doesn't reproduce any sound.

I think I have the same problem which was discussed in this thread [http://ubuntuforums.org/showthread.php?t=1561098](http://ubuntuforums.org/showthread.php?t=1561098)  but I don't see how a wireless driver can make my keyboard work.

The point is that now I'm using my WIFI thanks pytheas22 ( [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) ) but neither the fn key is working fine nor the PC is able to reproduce sounds.

So, Is it possible that Ubuntu takes the complete control of my keyboard? Should I change my distro? Or even worst... Should I come back to windows?

The specifications: Intel i3-330M (2.13 GHz), 64bits Windows 7, ATI Mobility Radeon 5470, Network controller: Broadcom Corporation Device 4727

Thanks

Nacho

---

### Post by Okso on 2010-09-08
Have you been able to find any solution yet to have the Fn key working? I'm in the same boat...

---

### Post by mentero on 2010-09-15
Hi, 

Same problem with the Fn key in HP G62 a35SS 

My daughter is using a HP G62 140ES with the same i3 330 processor, a similar keyboard layout, and everything worked out of the box with the exception of audio, solved with a ALSA update. Brightness, volume, play controls and even the led on the wifi key changes colour when asked for.
  
In theory the only difference between the two models is the graphic card, HD 5430 for 140ES and switchable HD 5470/Intel GMA HD (i915).

Any help will be appreciated,

mentero

(First post of a long term linux newbee)

---

### Post by xetani on 2010-10-01
Hello.
I have a G62-a50SM (i3-350m, HD 5470) and i have the same problem.
None of the Fn buttons work , the lock button right of F12 and all the hotkey buttons don't work either.
Xev and dmesg show no events on button press.
Im using Ubuntu 10.04 x64.

Also the wifi led indicator doesn't do anything, nor does the touchpad led. Although during the install of debian 5.0 the wifi led did turn on and off on F12 press, but the install didnt work due to intel gfx drivers so i didn't manage to actually test the hotkeys. None of the hotkeys work on openSUSE nor fedora 11.
They don't work on 32bit ubuntu either.

Another problem is that it doesn't show remaining battery nor remaining time to charge because acpi doesn't show the current power consumption so it cannot compute.
Other than those two everything works fine.

---

### Post by reinfallt on 2010-10-23
I just bought a G62-A31SO and have the same problem with the fn-key. BUT I don't think the problem is with the fn-key itself because for me it does work for the "insert/print screen" button. If I don't hold down the fn-key it does print screen. If I do hold down the fn-key it does insert. That would mean that the problem is with the other buttons and not with the fn-key. Please confirm that it is the same for you guys.

---

### Post by reinfallt on 2010-10-23
I FIXED IT!

Solution:
1. Go into BIOS
2. Go to "System Configuration"
3. Set "Action Keys Mode" to "Disabled"

Now all the "fn"-keys work for me at least :popcorn:

---

### Post by dneff87 on 2010-10-28
I have been having trouble with all of my function keys on a G62-222US on both 10.04 and now still on 10.10. The odd thing was that the volume keys always worked (but without pressing Fn)

After disabling the "Action Keys Mode" I have some interesting behaviors:
1) Volume keys now ONLY work with Fn
2) Other function keys now ALL show in xev for the first time, but:
3) The brightness keys and the screen selector key don't work, with or without Fn
4) The media player control keys (play/pause, next track, etc) now work with Fn, whereas they did not work before.

My guess is there is a significant problem with the way the BIOS and OS are communicating.

Hopefully this info helps bring us closer to some more solutions...

---

### Post by reinfallt on 2010-10-29
> **dneff87 said:**
> I have been having trouble with all of my function keys on a G62-222US on both 10.04 and now still on 10.10. The odd thing was that the volume keys always worked (but without pressing Fn)

After disabling the "Action Keys Mode" I have some interesting behaviors:
1) Volume keys now ONLY work with Fn
2) Other function keys now ALL show in xev for the first time, but:
3) The brightness keys and the screen selector key don't work, with or without Fn
4) The media player control keys (play/pause, next track, etc) now work with Fn, whereas they did not work before.

My guess is there is a significant problem with the way the BIOS and OS are communicating.

Hopefully this info helps bring us closer to some more solutions...

The brightness keys work for me at least. I haven't tried the screen selector since I never have an external monitor connected but it shows up in xev at least.

But if the brightness keys showed up in xev for you but didn't work in practice it might just be that the shortcuts are wrong and you have to manually set them up. In KDE at least it's possible to assign "Global Keyboard Shortcuts" for both screen brightness and display switching.

---

### Post by xetani on 2010-10-29
Disabling the "Action Keys Mode" doesn't do anything for me. Dmesg and Xev still show nothing on keypress. 

Ive also submitted a bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/661768](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/661768) .

Btw, could any of you check if dmesg or xev give output for Fn / shortcut keys and post? I have a version with i3-350m and hd 5470 but some of you may have different specs and because of that a different bios.

---

### Post by reinfallt on 2010-10-30
> **xetani said:**
> Disabling the "Action Keys Mode" doesn't do anything for me. Dmesg and Xev still show nothing on keypress. 

Ive also submitted a bug report [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/661768](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/661768) .

Btw, could any of you check if dmesg or xev give output for Fn / shortcut keys and post? I have a version with i3-350m and hd 5470 but some of you may have different specs and because of that a different bios.

I have the exact same hardware in my laptop. This is what my xev outputs for fn+(F1-F12). The key for turning off/on wireless (F12) doesn't send any key code but it still works.

```
KeyPress event, serial 34, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 265469, (105,114), root:(1066,137),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 265470, (105,114), root:(1066,137),
    state 0x40, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 265473, (105,114), root:(1066,137),
    state 0x40, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 265478, (105,114), root:(1066,137),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 34, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 34, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 35, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 35, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  4294967295 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   0   

KeyRelease event, serial 35, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 266772, (105,114), root:(1066,137),
    state 0x0, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 35, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 35, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  4294967295 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   0   

KeyRelease event, serial 37, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 266772, (105,114), root:(1066,137),
    state 0x0, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   2   0   0   

KeyRelease event, serial 37, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 267523, (105,114), root:(1066,137),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 37, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 39, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 39, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 39, synthetic NO, window 0x0,
    keys:  4294967295 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   2   0   0   

KeyRelease event, serial 39, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 267523, (105,114), root:(1066,137),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 39, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 39, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268044, (105,114), root:(1066,137),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 39, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268044, (105,114), root:(1066,137),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268045, (105,114), root:(1066,137),
    state 0x40, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268514, (105,114), root:(1066,137),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268518, (105,114), root:(1066,137),
    state 0x0, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268524, (105,114), root:(1066,137),
    state 0x0, keycode 173 (keysym 0x1008ff16, XF86AudioPrev), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268983, (105,114), root:(1066,137),
    state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 268987, (105,114), root:(1066,137),
    state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 269432, (105,114), root:(1066,137),
    state 0x0, keycode 174 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 269436, (105,114), root:(1066,137),
    state 0x0, keycode 174 (keysym 0x1008ff15, XF86AudioStop), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 269886, (105,114), root:(1066,137),
    state 0x0, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 269891, (105,114), root:(1066,137),
    state 0x0, keycode 171 (keysym 0x1008ff17, XF86AudioNext), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 40, synthetic NO, window 0x0,
    keys:  4294967295 0   0   0   0   0   0   0   0   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 270422, (105,114), root:(1066,137),
    state 0x0, keycode 122 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 40, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   8   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 270880, (105,114), root:(1066,137),
    state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 40, synthetic NO, window 0x5000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 40, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   2   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 40, synthetic NO, window 0x5000001,
    root 0xff, subw 0x0, time 271419, (105,114), root:(1066,137),
    state 0x0, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

This is my lshw if you can find something that differs:
```
reinfallt-hp
    description: Notebook
    product: HP G62 Notebook PC
    vendor: Hewlett-Packard
    version: 0497100000252710001020000
    serial: 4CZ0251JZT
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=4CAE7F20-A1F5-A184-D38C-0F267E161D1E
  *-core
       description: Motherboard
       product: 143A
       vendor: Hewlett-Packard
       physical id: 0
       version: 60.3E
       serial: 4CZ0251JZT
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.35 (09/06/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: EBJ21UE8BDS0-DJ-F
             vendor: ELPIDA
             physical id: 0
             serial: A0DE34DE
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: EBJ21UE8BDS0-DJ-F
             vendor: ELPIDA
             physical id: 1
             serial: A1DE34DE
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
          slot: CPU
          size: 933MHz
          capacity: 2266MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L3 cache
             physical id: 1c
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 1e
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 1f
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 1d
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:3000(size=4096) memory:c4400000-c44fffff ioport:a0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Manhattan [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:a0000000-afffffff(prefetchable) memory:c4400000-c441ffff ioport:3000(size=256) memory:c4440000-c445ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:36 memory:c4420000-c4423fff
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:34 memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:4050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:c4504000-c450400f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c450a000-c450a3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:35 memory:c4500000-c4503fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:2000(size=4096) memory:c3400000-c43fffff ioport:c0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 90:fb:a6:a8:b0:f3
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:32 ioport:2000(size=256) memory:c0410000-c0410fff(prefetchable) memory:c0400000-c040ffff(prefetchable) memory:c0420000-c043ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:1000(size=4096) memory:c2400000-c33fffff ioport:c1400000(size=16777216)
           *-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 78:e4:00:94:4f:79
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:18 memory:c2400000-c2403fff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:c4509000-c45093ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:33 ioport:4048(size=8) ioport:405c(size=4) ioport:4040(size=8) ioport:4058(size=4) ioport:4020(size=32) memory:c4508000-c45087ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0006
                serial: 5VJ6NFM4
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=533bba72
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 9af4-4dfa
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-10-22 18:55:38 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: f8fe67fb-d3d1-2849-a6bd-2d7a33d4a356
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-10-22 18:56:01 filesystem=ntfs state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 06804428-732b-4ab6-a40d-44461f056177
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-24 10:51:12 filesystem=ext4 lastmountpoint=/&#65533;|C>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;|C>&#65533;&#65533;&#65533;&#65533;%Q&#65533;&#65533;&#65533;@e@>&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;ps&#65533;&#65533;&#65533;&#65533;&#65533;X#xO&#65533; modified=2010-10-29 10:07:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-30 12:22:58 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 355GiB
                   capacity: 355GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 353GiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1937MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L633N
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0300
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c4506000-c45060ff ioport:4000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:7f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:7f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:7f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:7f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:7f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:7f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
  *-battery
       product: MU06047
       vendor: 13-54
       physical id: 1
       slot: In the back
       capacity: 47000mWh
       configuration: voltage=10.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by reinfallt on 2010-10-30
I just realized that the "?" on F1 and the screen selector on F4 are sending the wrong key codes. The "?" is sending a "Super_L" a.k.a. the left "windows key". And the screen selector is sending just a regular "p".

---

### Post by xetani on 2010-10-30
Ok there are 2 bios updates on the page for my model and they are the same bioses for most or all g62 models with intel. 
The one i was using all along was F.0B A.
The keys dont work on that one.
The one you are using is F.35 A.
Ive installed that one now, ubuntu registers all keys in xev now and they work... but my screen is blank on boot and it only works if i connect an external monitor. When i do nether windows or linux detects my ati nor intel graphics and it uses VGA. I cant see the 2 gfx in /proc/acpi , instead i see just VGA. Still trying to fix it since if hp posted the bios update for my model, it is supposed to work for my model...

---

### Post by xetani on 2010-10-30
Oh yea and lshw displays everything the same except that u got 4 gigs of memory and ive got 3, and it _doesnt show display_. I guess thats why my graphics dont work, but i dont get it, its the same intel gpu and the same ati radeon gpu.

---

### Post by reinfallt on 2010-10-30
Yeah, I forgot that I had upgraded my bios. I did that to see if it would fix my touchpad issues, which it didn't.

Weird that your graphics cards won't work. The only issues I have is that I can only use the intel card with linux since the fglrx drivers doesn't support switchable graphics. Also the x-server refuses to start at times but usually works after a reboot so I can live with it. Win 7 works flawlessly though and I can switch between the different GPU's.

---

### Post by xetani on 2010-10-30
Yeah the only difference between the two bioses is that on one the keys and the battery work and on the other they dont. It seams that by flashing the other bios ive made both my graphics adapters unusable as bios doesnt return the acpi for linux nor windows. Going to the old bios doesnt help, and diagnostics say all is fine. Looks like ill need to contact hp support, because flashing a bios that was dled from their site for my model should have really worked and must not have caused any damage. Ive tried everything , and i cant find any useful info about the problem online.

---

### Post by pol90 on 2010-11-18
Just bought HP G62-a35ss and installed Ubuntu 10.10. Had the same problem and just downloaded the BIOS update (sp5xxxx.exe) from HP site and run it on W7 and now, bum, hotkeys work flawlessly except the media key, that everybody says it's dead.

ALSA problem didn't affect me 'cause 10.10 comes with an updated version.

pd. Now wireless key goes on and off, but it does nothing.

---

### Post by xetani on 2010-11-23
Just a small warning,
Do not update your bios to F.35 A
It did fix the keys and battery issues for me, but it disabled my gfx cards. I sent it in for repair and they told me hp is aware that that bios may brake your motherboard and told me to wait for the new bios.
Btw i guess reinfallt was lucky, he has the same motherboard but he successfully updated the bios to that version.
Anyway, im not gonna risk it again, waiting for the new bios version...

---

### Post by dneff87 on 2011-01-31
Hi all,

I haven't checked in in a while because I figured I'd just wait for a new BIOS version. I flashed my BIOS through my windows partition last night, and now the brightness keys are working. The new bios version is F.17 on my G62-222US. I'm running 2.6.35-25-generic on  10.10

Apparently good things do come to those who wait...

I'm not too well versed in these things, so I doubt I'll be able to give you any more help than just reporting my experience.

Good luck!

---

### Post by hanciong on 2011-02-02
I have the same problem like you. I have HP G62 100SL. The sound doesn't work. after updating ALSA, the sound  works..... for a while. After some other update (from update manager),  the sound doesn't work again. why is this? and then if I run firefox,  other video programs seem don't work (for example like VLC or totem).  The movie I play there just doesn't play. In order for them to work, I  must close  firefox first. how to fix this? Thanx a lot

---

