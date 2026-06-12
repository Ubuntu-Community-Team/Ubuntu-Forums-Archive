---
title: "Graphics messed up after installing &gt; 4 GB memory"
date: 2016-01-21
forum: Hardware
---

### Post by bertram2 on 2016-01-21
Hi all,

I'm running Ubuntu MATE 15.10 64 bit on a computer with an ASUS P5G41T-M LE motherboard and onboard graphics. It's already a couple of years old, but has been doing it's job really well.

However, I recently bought a 4 GB memory bank (compatible to the mainboard) and installed it along with the previously installed 2 GB bank. This led to the graphics being messed up on the desktop environment:
[ATTACH=CONFIG]266874[/ATTACH]
The problem seems to occur as soon as there's more than 4 GB memory installed. Using only one of the two memories there's no problem at all, however, installing both (and therefore having 6 GB of RAM available) leads to the graphical environment being unusable.

dmesg gives the following output which might be related to the problem:
```
[  146.000438] ------------[ cut here ]------------
[  146.000467] WARNING: CPU: 0 PID: 1221 at /build/linux-AFqQDb/linux-4.2.0/drivers/gpu/drm/i915/i915_gem.c:5269 i915_gem_track_fb+0x129/0x140 [i915]()
[  146.000469] WARN_ON(!(old->frontbuffer_bits & frontbuffer_bits))
[  146.000470] Modules linked in:
[  146.000472]  nvram msr pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) binfmt_misc joydev input_leds snd_hda_codec_realtek snd_hda_codec_generic snd_hda_intel coretemp snd_hda_codec kvm_intel snd_hda_core snd_hwdep kvm snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer serio_raw snd soundcore asus_atk0110 8250_fintek lpc_ich shpchp mac_hid parport_pc ppdev lp parport autofs4 i915 hid_generic video uas i2c_algo_bit psmouse pata_acpi drm_kms_helper 3c59x usb_storage mii drm atl1c usbhid hid
[  146.000510] CPU: 0 PID: 1221 Comm: Xorg Tainted: G           OE   4.2.0-23-generic #28-Ubuntu
[  146.000512] Hardware name: System manufacturer System Product Name/P5G41T-M LE, BIOS 1001    08/02/2012
[  146.000514]  0000000000000000 00000000d6eb957a ffff8800d5817ac8 ffffffff817e94c9
[  146.000517]  0000000000000000 ffff8800d5817b20 ffff8800d5817b08 ffffffff8107b3d6
[  146.000520]  ffff880035b92180 0000000000000010 ffff880195784000 ffff880195784000
[  146.000523] Call Trace:
[  146.000528]  [<ffffffff817e94c9>] dump_stack+0x45/0x57
[  146.000532]  [<ffffffff8107b3d6>] warn_slowpath_common+0x86/0xc0
[  146.000535]  [<ffffffff8107b465>] warn_slowpath_fmt+0x55/0x70
[  146.000552]  [<ffffffffc01b4ec9>] i915_gem_track_fb+0x129/0x140 [i915]
[  146.000573]  [<ffffffffc01fd157>] intel_prepare_plane_fb+0xe7/0x1a0 [i915]
[  146.000581]  [<ffffffffc0119009>] drm_atomic_helper_prepare_planes+0x59/0xe0 [drm_kms_helper]
[  146.000600]  [<ffffffffc00909e5>] ? drm_atomic_check_only+0x215/0x540 [drm]
[  146.000620]  [<ffffffffc020de12>] intel_atomic_commit+0x42/0x100 [i915]
[  146.000633]  [<ffffffffc0090d47>] drm_atomic_commit+0x37/0x60 [drm]
[  146.000640]  [<ffffffffc011a677>] drm_atomic_helper_plane_set_property+0x87/0xc0 [drm_kms_helper]
[  146.000651]  [<ffffffffc007e739>] ? _object_find+0x69/0xa0 [drm]
[  146.000663]  [<ffffffffc007efbd>] drm_mode_plane_set_obj_prop+0x2d/0x90 [drm]
[  146.000676]  [<ffffffffc0085a76>] drm_mode_obj_set_property_ioctl+0x1c6/0x270 [drm]
[  146.000685]  [<ffffffffc0075495>] drm_ioctl+0x125/0x610 [drm]
[  146.000689]  [<ffffffff8123e8b6>] ? fsnotify+0x316/0x4a0
[  146.000701]  [<ffffffffc00858b0>] ? drm_mode_obj_get_properties_ioctl+0xa0/0xa0 [drm]
[  146.000705]  [<ffffffff81210aa5>] do_vfs_ioctl+0x295/0x480
[  146.000708]  [<ffffffff811ff875>] ? __sb_end_write+0x35/0x70
[  146.000710]  [<ffffffff811fd4aa>] ? vfs_write+0x15a/0x1a0
[  146.000712]  [<ffffffff81210d09>] SyS_ioctl+0x79/0x90
[  146.000716]  [<ffffffff817f02b2>] entry_SYSCALL_64_fastpath+0x16/0x75
[  146.000718] ---[ end trace 7ee148c153c6d552 ]---
```

Xorg log doesn't show anything unusual, but I'll attach it as well.

I'm not sure whether this is the right place to post my problem, since it has to do with Desktop Environments as well, so any admin place feel free to move the thread accordingly. If there's any more information you need to know, I'm happy to provide it, but since I've already spent a couple of weeks trying to track down the problem - or at least find any hints on how to solve it - without success, I'm hoping for some ideas in this forum.

Thank's for any help and best regards,

Bertram

---

### Post by Yellow Pasque on 2016-01-21
It sort of looks like this bug: [https://bugzilla.kernel.org/show_bug.cgi?id=106401](https://bugzilla.kernel.org/show_bug.cgi?id=106401)

Have you tried a newer kernel? (Note: the virtualbox kernel package may cause issues for you)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.4-wily/)

---

### Post by ajgreeny on 2016-01-21
Are both memory modules the same make, speed and type?  Incompatibility can occur if they are different in any way, perhaps borne out by the fact that either module is fine on its own.

Let's see the output of terminal command [/code]sudo lshw -c memory[/code] with both modules installed which will give us all the details of both.

---

### Post by bertram2 on 2016-01-23
Thank's for your replies.

@Temüjin:
I've updated the kernel (running now 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux) but that didn't change the results. Blacklisting all virtualbox related kernel modules didn't help either.

@ajgreeny:
Both modules are at same speed, even same manufacturer and series, but different sizes (Kingston KVR1333D3N9/4G and Kingston KVR1333/D3N9/2g).

Here a few more outputs:
lshw -c memory
```
  *-memory
       description: System memory
       physical id: 0
       size: 5901MiB
```
free -h
```
             total       used       free     shared    buffers     cached
Mem:          5,8G       412M       5,4G        29M        49M       214M
-/+ buffers/cache:       148M       5,6G
Swap:         9,3G         0B       9,3G
```
dmidecode --type 17
```
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM A1
    Bank Locator: BANK0
    Type: Other
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0028
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM B1
    Bank Locator: BANK1
    Type: Other
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1
```

I might point out again, that this is an issue when using onboard graphics. As soon as use another graphics card the problems disappear. So this could be some problem of the mainboard as well (which then probably wouldn't be able to be solved on the linux side)...

---

### Post by Yellow Pasque on 2016-01-23
No, I meant trying a 4.4 kernel as shown in the links I provided as opposed to just installing a regular update. The bug I linked to will be fixed in that kernel

---

### Post by bertram2 on 2016-01-23
Just installed the 4.4 kernel, however, as soon as the xserver starts the monitor doesn't receive any signal any more. (Switching to console via CTRL+ALT+F1 gives me the screen back...) There are a couple of bug reports on issues with the i915 driver and the 4.4 kernel, but dmesg doesn't give me any i915-related error.

---

