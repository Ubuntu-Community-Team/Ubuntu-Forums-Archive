---
title: "Lenovo E560 CPU Performance"
date: 2016-01-10
forum: Hardware
---

### Post by Zavation on 2016-01-10
Hi all,

I'm planning on buying the Lenovo E560 laptop, purely because I can get an i7 with 16GB RAM at a decent price.

Upon my research I found that one person in particular on the thinkpad forum, said that they were having issues with the CPU. This is specifically linked with the i915 kernel module.

The link to the post I'm referring to is this: [http://forum.thinkpads.com/viewtopic.php?t=118979](http://forum.thinkpads.com/viewtopic.php?t=118979) - post by dkasak. 

I was just curious to see if anyone else has this laptop / would know if the CPU issues would be resolved by now. Even if I had to use a RC Kernel version to fix the issues.

Thanks!

p.s here is the log that he added to his post:

```
[COLOR=#006600][FONT=Monaco][   62.542089] WARNING: CPU: 1 PID: 2161 at drivers/gpu/drm/i915/intel_runtime_pm.c:551 skl_set_power_well+0x1e0/0x897 [i915]()[/FONT][/COLOR][   62.542092] DC6 already programmed to be disabled.
[   62.542094] Modules linked in: joydev r8712u(C) snd_hda_codec_hdmi iTCO_wdt iTCO_vendor_support intel_rapl iosf_mbi x86_pkg_temp_thermal 
intel_powerclamp coretemp kvm_intel uvcvideo videobuf2_vmalloc kvm videobuf2_memops crct10dif_pclmul crc32_pclmul videobuf2_core 
v4l2_common crc32c_intel videodev aesni_intel media lrw glue_helper ablk_helper cryptd microcode nd_hda_codec_conexant btusb 
snd_hda_codec_generic btrtl btbcm e1000e btintel input_leds efivars psmouse pcspkr serio_raw iwlwifi i2 c_i801 bluetooth cfg80211 snd_hda_intel 
shpchp thinkpad_acpi nvram tpm_crb fjes tpm sch_fq_codel zfs(PO) zunicode(PO) zcommon(PO) znvpair(PO) spl(O) zavl(PO) efivarfs  ipv6 
virtio_pci virtio_scsi virtio_blk virtio_net virtio_console virtio_balloon virtio_ring virtio xts gf128mul aes_x86_64 sha512_generic 
sha256_generic
[   62.542156]  
iscsi_tcp libiscsi_tcp tg3 e1000 fuse overlay xfs nfs lockd grace sunrpc jfs reiserfs ext4 jbd2 ext2 mbcache firewire_core sl811_hcd 
xhci_plat_hcd ohc i_pci ohci_hcd uhci_hcd ehci_pci ehci_hcd sx8 imm parport pata_pcmcia pcmcia hid_generic snd_hda_codec 
snd_hda_core snd_hwdep ptp pps_core snd_pcm snd_timer snd i915 drm_kms_helper drm intel_gtt xhci_pci agpgart fb_sys_fops 
syscopyarea xhci_hcd sysfillrect sysimgblt i2c_algo_bit
[   62.542185] CPU: 1 PID: 2161 Comm: pulseaudio Tainted: P        WC O    4.3.0-sabayon #1
[   62.542187] Hardware name: LENOVO 20EVCTO1WW/20EVCTO1WW, BIOS R00ET32W (1.07 ) 10/14/2015
[   62.542189]  0000000000000000 ffff88021a75b828 ffffffff812d03ec ffff88021a75b870
[   62.542192]  ffff88021a75b860 ffffffff81053378 ffffffffa00ebd5e ffff880237be0000
[   62.542195]  ffffffffa0195f90 000000003000000f ffff880237f05800 ffff88021a75b8c8
[   62.542198] Call Trace:
[   62.542201]  [<ffffffff812d03ec>] dump_stack+0x44/0x55
[   62.542205]  [<ffffffff81053378>] warn_slowpath_common+0x95/0xae
[   62.542220]  [<ffffffffa00ebd5e>] ? skl_set_power_well+0x1e0/0x897 [i915]
[   62.542224]  [<ffffffff810533d4>] warn_slowpath_fmt+0x43/0x4b
[   62.542237]  [<ffffffffa00ebd5e>] skl_set_power_well+0x1e0/0x897 [i915]
[   62.542252]  [<ffffffffa00ec430>] skl_power_well_enable+0xe/0x10 [i915]
[   62.542265]  [<ffffffffa00ec650>] intel_display_power_get+0x99/0xc4 [i915]
[   62.542282]  [<ffffffffa011ab34>] i915_audio_component_get_power+0x19/0x1b [i915]
[   62.542288]  [<ffffffffa01f1ed6>] snd_hdac_display_power+0x92/0xf4 [snd_hda_core]
[   62.542293]  [<ffffffffa0201990>] ? hda_call_codec_resume+0x110/0x110 [snd_hda_codec]
[   62.542295]  [<ffffffffa0905169>] 0xffffffffa0905169
[   62.542301]  [<ffffffffa0206b8e>] azx_link_power+0x1f/0x21 [snd_hda_codec]
[   62.542306]  [<ffffffffa01eeaef>] snd_hdac_link_power+0x2e/0x30 [snd_hda_core]
[   62.542311]  [<ffffffffa02019a2>] hda_codec_runtime_resume+0x12/0x43 [snd_hda_codec]
[   62.542315]  [<ffffffff813dd04e>] __rpm_callback+0x32/0x59
[   62.542319]  [<ffffffff813dd0d1>] rpm_callback+0x5c/0x74
[   62.542324]  [<ffffffffa0201990>] ? hda_call_codec_resume+0x110/0x110 [snd_hda_codec]
[   62.542327]  [<ffffffff813ddcdf>] rpm_resume+0x332/0x3d7
[   62.542330]  [<ffffffff813dddd4>] __pm_runtime_resume+0x50/0x6b
[   62.542334]  [<ffffffffa01ee9a1>] snd_hdac_power_up+0xe/0x10 [snd_hda_core]
[   62.542340]  [<ffffffffa02073e9>] azx_pcm_open+0x176/0x252 [snd_hda_codec]
[   62.542345]  [<ffffffffa01e219e>] snd_pcm_open_substream+0x76/0xdc [snd_pcm]
[   62.542352]  [<ffffffffa01e22b1>] snd_pcm_open+0xad/0x1c5 [snd_pcm]
[   62.542355]  [<ffffffff8106ed30>] ? wake_up_q+0x51/0x51
[   62.542360]  [<ffffffffa01e2465>] snd_pcm_playback_open+0x3b/0x5e [snd_pcm]
[   62.542364]  [<ffffffffa0092462>] snd_open+0x12b/0x137 [snd]
[   62.542368]  [<ffffffff81139f28>] chrdev_open+0x130/0x153
[   62.542371]  [<ffffffff81139df8>] ? cdev_put+0x1e/0x1e
[   62.542374]  [<ffffffff81134a90>] do_dentry_open+0x1af/0x2ae
[   62.542378]  [<ffffffff8113587e>] vfs_open+0x54/0x5b
[   62.542381]  [<ffffffff81141b6d>] path_openat+0xb55/0xe58
[   62.542386]  [<ffffffff8114300d>] do_filp_open+0x48/0x9e
[   62.542390]  [<ffffffff81147e4a>] ? dput+0x26/0x1b8
[   62.542393]  [<ffffffff81137b02>] ? ____fput+0x9/0xb
[   62.542395]  [<ffffffff81068300>] ? task_work_run+0x6a/0x7b
[   62.542398]  [<ffffffff8111d952>] ? kmem_cache_alloc+0x2b/0x13b
[   62.542402]  [<ffffffff81135b8d>] do_sys_open+0x146/0x1d5
[   62.542405]  [<ffffffff81135b8d>] ? do_sys_open+0x146/0x1d5
[   62.542409]  [<ffffffff81135c35>] SyS_open+0x19/0x1b
[   62.542413]  [<ffffffff818b04b6>] entry_SYSCALL_64_fastpath+0x16/0x75
[   62.542416] ---[ end trace 4e0675973f646f3a ]---
[   65.776740] [drm:skl_set_power_well [i915]] *ERROR* CSR firmware not ready (2)
[   78.934536] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-16.ucode failed with error -2
[   78.934547] iwlwifi 0000:01:00.0: Falling back to user helper
[  137.816117] [drm:i915_hangcheck_elapsed [i915]] *ERROR* Hangcheck timer elapsed... render ring idle
[  138.981767] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[  138.981781] iwlwifi 0000:01:00.0: Falling back to user helper
[  199.028781] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2
[COLOR=#006600][FONT=Monaco][  199.028794] iwlwifi 0000:01:00.0: Falling back to user helper[/FONT][/COLOR]
```

---

### Post by gedas0220 on 2016-01-11
Hi,
I'm running Ubuntu mate 16.04 on my e560 i7 without any issues, only fingerprint scanner doesn't work. Before I tried to use Mint 17.03 Rosa linux with kernel 4.3 but it was running unstable for me.

---

### Post by Zavation on 2016-01-11
Thanks! So you do think 4.4 is going to be the optimal kernel for it? Also, how do you find the laptop. i.e build quality?

---

### Post by gedas0220 on 2016-01-12
Like I said before, with ubuntu mate 16.04 and kernel ver. 4.3.0-5-generic I do not have any complaints. 
So, 4.4 will be for sure the optimal :) 

>  how do you find the laptop. i.e build quality?

I think you can find a more detailed reviews on the net, but
I like my e560.. It's fast, good quality screen, works quietly and so one..

---

### Post by gedas0220 on 2016-01-12
Update: fingerprint scaner works well with fingerprint-gui

---

