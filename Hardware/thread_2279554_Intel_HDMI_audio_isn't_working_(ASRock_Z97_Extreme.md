---
title: "Intel HDMI audio isn't working (ASRock Z97 Extreme 6)"
date: 2015-05-24
forum: Hardware
---

### Post by KillerKelvUK on 2015-05-24
So I've had this motherboard for a couple of months now, bought it because of its virtualisation capabilities (namely vt-d).  Out of the box Ubuntu 14.10 and 15.04 work fine with HDMI audio but as soon as I enable the virtualisation capabilities via a kernel parameter 'intel_iommu=on' then HDMI audio stops working and I have to revert to analog.

There are some kernel bug reports that suggest this is a known issue and has been for quite sometime although my efforts to resolve using that has failed due to lack of affected users warranting dev support.

Anyway's I recently upgraded to 15.04 using the 3.19-18 kernel and noticed some additional dmesg outputs that potentially shed more light on this and was wondering if someone could take a look at give me a steer on what I need to focus on (i.e. the problem) as I'm not very experienced with this type of problem...

dmesg lines I've just seen using latest kernel...
```

[    2.496378] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    2.496680] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    2.498252] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    2.509067] sound hdaudioC1D0: ALC1150: SKU not ready 0x00000000
[    2.509536] sound hdaudioC1D0: autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    2.509539] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.509540] sound hdaudioC1D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    2.509541] sound hdaudioC1D0:    mono: mono_out=0x0
[    2.509543] sound hdaudioC1D0:    dig-out=0x1e/0x0
[    2.509544] sound hdaudioC1D0:    inputs:
[    2.509546] sound hdaudioC1D0:      Front Mic=0x19
[    2.509547] sound hdaudioC1D0:      Rear Mic=0x18
[    2.509549] sound hdaudioC1D0:      Line=0x1a
[    2.513308] Could not create debugfs 'switch_mm' directory
[    2.513311] Could not create debugfs 'i915_context_free' directory
[    2.513313] Could not create debugfs 'i915_context_create' directory
[    2.513315] Could not create debugfs 'i915_ppgtt_release' directory
[    2.513317] Could not create debugfs 'i915_ppgtt_create' directory
[    2.513320] Could not create debugfs 'intel_gpu_freq_change' directory
[    2.513322] Could not create debugfs 'i915_reg_rw' directory
[    2.513325] Could not create debugfs 'i915_flip_complete' directory
[    2.513327] Could not create debugfs 'i915_flip_request' directory
[    2.513329] Could not create debugfs 'i915_ring_wait_end' directory
[    2.513331] Could not create debugfs 'i915_ring_wait_begin' directory
[    2.513333] Could not create debugfs 'i915_gem_request_wait_end' directory
[    2.513335] Could not create debugfs 'i915_gem_request_wait_begin' directory
[    2.513337] Could not create debugfs 'i915_gem_request_complete' directory
[    2.513339] Could not create debugfs 'i915_gem_request_retire' directory
[    2.513349] Could not create debugfs 'i915_gem_request_add' directory
[    2.513352] Could not create debugfs 'i915_gem_ring_flush' directory
[    2.513354] Could not create debugfs 'i915_gem_ring_dispatch' directory
[    2.513356] Could not create debugfs 'i915_gem_ring_sync_to' directory
[    2.513358] Could not create debugfs 'i915_gem_evict_vm' directory
[    2.513361] Could not create debugfs 'i915_gem_evict_everything' directory
[    2.513363] Could not create debugfs 'i915_gem_evict' directory
[    2.513365] Could not create debugfs 'i915_gem_object_destroy' directory
[    2.513367] Could not create debugfs 'i915_gem_object_clflush' directory
[    2.513370] Could not create debugfs 'i915_gem_object_fault' directory
[    2.513372] Could not create debugfs 'i915_gem_object_pread' directory
[    2.513374] Could not create debugfs 'i915_gem_object_pwrite' directory
[    2.513377] Could not create debugfs 'i915_gem_object_change_domain' directory
[    2.513396] Could not create debugfs 'i915_vma_unbind' directory
[    2.513399] Could not create debugfs 'i915_vma_bind' directory
[    2.513401] Could not create debugfs 'i915_gem_object_create' directory
[    2.513403] Could not create debugfs 'i915_pipe_update_end' directory
[    2.513405] Could not create debugfs 'i915_pipe_update_vblank_evaded' directory
[    2.513407] Could not create debugfs 'i915_pipe_update_start' directory
[    2.514160] snd_hda_intel 0000:00:03.0: Cannot turn on display power on i915
[    2.518588] Switched to clocksource tsc
[    2.520752] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[    2.531263] AVX2 version of gcm_enc/dec engaged.
[    2.531265] AES CTR mode by8 optimization enabled
[    2.544293] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[    2.544348] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    2.544415] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    2.544471] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[    2.544525] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input14
[    2.544593] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input15

```

lspci...

```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (2) I218-V
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1c.6 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 7 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
03:00.0 PCI bridge: ASMedia Technology Inc. Device 1184
04:01.0 PCI bridge: ASMedia Technology Inc. Device 1184
04:03.0 PCI bridge: ASMedia Technology Inc. Device 1184
04:05.0 PCI bridge: ASMedia Technology Inc. Device 1184
04:07.0 PCI bridge: ASMedia Technology Inc. Device 1184
06:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
07:00.0 Multimedia video controller: Spin Master Ltd. Device 3038 (rev 01)
08:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)
09:00.0 USB controller: ASMedia Technology Inc. ASM1042A USB 3.0 Host Controller

```

Any pointers would be appreciated.

---

### Post by dino99 on 2015-05-24
it is a known issue, but also propose a partial workaround

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121)

and maybe some other tweaks to test (does not know if it is still relevant)
[https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

and some more explanations
[https://wiki.debian.org/VGAPassthrough](https://wiki.debian.org/VGAPassthrough)

---

### Post by KillerKelvUK on 2015-05-24
> **dino99 said:**
> it is a known issue, but also propose a partial workaround

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1428121)

Hey, thats my bug report for this problem initially i.e. the one that hasn't received much attention due to the few users affected.  The *work-around* to enable audio actually disables the IOMMU functions which effectively breaks virtualisation (vt-x & vt-d) and so for me this isn't an option as I need virtualisation more than I need HDMI audio.

Was hoping the new dmesg output I posted might show a different way of attacking the problem?

---

