---
title: "Intel HDA failure on Intrepid"
date: 2008-12-01
forum: Hardware
---

### Post by theirishfozz on 2008-12-01
Hi everyone.

I've been using OSS for months. When I installed ubuntu Alsa was working but I couldn't get it working other than on headphones so I switched to OSS. Recently I upgraded my kernel and OSS stopped working so Im taking this as an opportunity to switch to ALSA. 

After trying a number of things I download the latest (as of yesterday) alsa-driver, alsa-utils, alsa-lib and alsa-oss source packages from the ALSA site, un-tarred, configured, made and installed each one. No problems. I ran ./snddevices in the driver directory and it ran fine. 

I rebooted, depmod etc and tried to load snd-hda-intel and I got this message

```
FATAL: Error inserting snd (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.27-10-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Here is what dmesg reports about it:

```
[ 2222.990479] snd: Unknown symbol unregister_sound_special
[ 2222.991452] snd: Unknown symbol register_sound_special_device
[ 2222.994042] snd: Unknown symbol sound_class
[ 2223.036471] snd_hwdep: Unknown symbol snd_info_register
[ 2223.036824] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 2223.037116] snd_hwdep: Unknown symbol snd_info_free_entry
[ 2223.037439] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 2223.037738] snd_hwdep: Unknown symbol snd_verbose_printk
[ 2223.038006] snd_hwdep: Unknown symbol snd_register_oss_device
[ 2223.038285] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 2223.038554] snd_hwdep: Unknown symbol snd_card_file_add
[ 2223.038886] snd_hwdep: Unknown symbol snd_iprintf
[ 2223.039158] snd_hwdep: Unknown symbol snd_major
[ 2223.039598] snd_hwdep: Unknown symbol snd_unregister_device
[ 2223.039887] snd_hwdep: Unknown symbol snd_device_new
[ 2223.040167] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 2223.040508] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 2223.040799] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 2223.041105] snd_hwdep: Unknown symbol snd_card_file_remove
[ 2223.041374] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 2223.062598] snd_timer: Unknown symbol snd_info_register
[ 2223.062972] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2223.063297] snd_timer: Unknown symbol snd_info_free_entry
[ 2223.063849] snd_timer: Unknown symbol snd_verbose_printk
[ 2223.064300] snd_timer: Unknown symbol snd_iprintf
[ 2223.064700] snd_timer: Unknown symbol snd_ecards_limit
[ 2223.065111] snd_timer: Unknown symbol snd_oss_info_register
[ 2223.065380] snd_timer: Unknown symbol snd_unregister_device
[ 2223.065695] snd_timer: Unknown symbol snd_device_new
[ 2223.066300] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2223.103961] snd: Unknown symbol unregister_sound_special
[ 2223.104938] snd: Unknown symbol register_sound_special_device
[ 2223.107523] snd: Unknown symbol sound_class
[ 2223.112826] snd_timer: Unknown symbol snd_info_register
[ 2223.113186] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2223.113503] snd_timer: Unknown symbol snd_info_free_entry
[ 2223.114050] snd_timer: Unknown symbol snd_verbose_printk
[ 2223.114402] snd_timer: Unknown symbol snd_iprintf
[ 2223.114804] snd_timer: Unknown symbol snd_ecards_limit
[ 2223.115200] snd_timer: Unknown symbol snd_oss_info_register
[ 2223.115472] snd_timer: Unknown symbol snd_unregister_device
[ 2223.115791] snd_timer: Unknown symbol snd_device_new
[ 2223.116429] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2223.117866] snd_pcm: Unknown symbol snd_info_register
[ 2223.118236] snd_pcm: Unknown symbol snd_info_create_module_entry
[ 2223.118741] snd_pcm: Unknown symbol snd_timer_notify
[ 2223.119095] snd_pcm: Unknown symbol snd_timer_interrupt
[ 2223.119374] snd_pcm: Unknown symbol snd_info_free_entry
[ 2223.119648] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[ 2223.119992] snd_pcm: Unknown symbol snd_info_get_str
[ 2223.120696] snd_pcm: Unknown symbol snd_verbose_printk
[ 2223.121263] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[ 2223.121546] snd_pcm: Unknown symbol snd_card_file_add
[ 2223.121967] snd_pcm: Unknown symbol snd_iprintf
[ 2223.122399] snd_pcm: Unknown symbol snd_major
[ 2223.123247] snd_pcm: Unknown symbol snd_unregister_device
[ 2223.123560] snd_pcm: Unknown symbol snd_timer_new
[ 2223.123832] snd_pcm: Unknown symbol snd_device_new
[ 2223.124342] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[ 2223.124938] snd_pcm: Unknown symbol snd_lookup_minor_data
[ 2223.125313] snd_pcm: Unknown symbol snd_info_create_card_entry
[ 2223.125587] snd_pcm: Unknown symbol snd_power_wait
[ 2223.125908] snd_pcm: Unknown symbol snd_device_free
[ 2223.126377] snd_pcm: Unknown symbol snd_card_file_remove
[ 2223.126649] snd_pcm: Unknown symbol snd_register_device_for_dev
[ 2223.127205] snd_pcm: Unknown symbol snd_device_register
[ 2223.127494] snd_pcm: Unknown symbol snd_info_get_line
[ 2223.129434] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[ 2223.129599] snd_hda_intel: Unknown symbol snd_ctl_add
[ 2223.129756] snd_hda_intel: Unknown symbol snd_pcm_new
[ 2223.129882] snd_hda_intel: Unknown symbol snd_jack_report
[ 2223.129980] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 2223.130087] snd_hda_intel: Unknown symbol snd_card_register
[ 2223.130185] snd_hda_intel: Unknown symbol snd_card_free
[ 2223.130283] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2223.130381] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 2223.130588] snd_hda_intel: Unknown symbol snd_add_device_sysfs_file
[ 2223.130818] snd_hda_intel: Unknown symbol snd_ctl_remove
[ 2223.130916] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 2223.131014] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[ 2223.131145] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 2223.131354] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 2223.131613] snd_hda_intel: Unknown symbol snd_component_add
[ 2223.131716] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[ 2223.131839] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[ 2223.131946] snd_hda_intel: Unknown symbol snd_card_new
[ 2223.132044] snd_hda_intel: Unknown symbol snd_iprintf
[ 2223.132163] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 2223.132261] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 2223.132392] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 2223.132499] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 2223.132597] snd_hda_intel: Unknown symbol snd_jack_new
[ 2223.132695] snd_hda_intel: Unknown symbol snd_hwdep_new
[ 2223.132870] snd_hda_intel: Unknown symbol snd_ctl_notify
[ 2223.132968] snd_hda_intel: Unknown symbol snd_ctl_boolean_stereo_info
[ 2223.133081] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 2223.133200] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 2223.133385] snd_hda_intel: Unknown symbol snd_device_new
[ 2223.133483] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[ 2223.133630] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 2223.133770] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 2223.133868] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 2223.134111] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 2223.134342] snd_hda_intel: Unknown symbol snd_device_free
[ 2223.134511] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 2223.134609] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[ 2223.134803] snd_hda_intel: Unknown symbol snd_pcm_format_width

```

aplay -l works, but lists no devices

there is no /proc/asound directory (or any kind)

```
uname -r: 2.6.27-10-generic
```

lspci entry:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Mitac Device 8227
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```

I initially tried to install the source using module-assistant but that crashed every time with this message:

(couldn't copy)
```
/usr/src/modules/alsa-driver/acore/info.c:90: error:implicit declaration
[/usr/src/modules/alsa-driver/acore/info.o] error 1
[/usr/src/modules/alsa-driver/acore] error 2
[_module_/usr/src/modules/alsa-driver] error 2

```

I've done lots of searching on this topic but cant seem to find other people with the same issue. A lot of posts seem at least a year old which is odd.

Anyway, any help would be appreciated.

thanks
Fozz

---

### Post by cariboo on 2008-12-01
I would suggest using the alsa packages from the repositories, if you still have the source directories you should be able to uninstall the self compiled programs.

Jim

---

### Post by theirishfozz on 2008-12-01
Thanks for the reply. Hmmm, I started out trying to do that following the comprehensive sound guide thingey.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=alsa+oss](http://ubuntuforums.org/showthread.php?t=766683&highlight=alsa+oss)
and
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but it didn't work. The sound problems guide suggested building from source which I did using module-assistant (which failed) so I downloaded manually. I dont really know what to do. Alsa and OSS both dont work. :(

---

### Post by markbuntu on 2008-12-02
You probably need to get rid of OSS4 before installing ALSA again because now they are both misinstalled.

---

### Post by theirishfozz on 2008-12-02
My hero. I managed to find an oss remove script and got rid of it. Now I can once again access the soundproperties panel (was crashing before) and the gstreamer volume icon has reappeared (good sign). Still so sound though.

When I run aplay -l the list is still empty. 

/proc/asound/cards says no sound cards.

I CAN modprobe snd-hda-intel (correct module) perfectly, no problems

The only dmesg entry relating to alsa or snd is from startup relating to SPDIF in some way (not marked as an error).

I can run alsaconf which returns a success and detects my card supposedly although Im not to sure its working correctly.

The gstreamer icon is marked as muted and any attempt to access it (double click or preferences) results in errors (no volume control plugins or devices found etc)

running alsamixer returns "No mixer elems found".

I've tried reinstalling the drivers and restarting quite a few times.

I still cant install the source using module-assistant. That still returns an error for some reason. Weird.


Thanks for your help so far. Seeing as I have a "working" module (i.e.no visible errors..lol) do either of you think I should try what jim said? Now that I have OSS removed fully perhaps I should try downloading the alsa packages rather than compiling?

---

### Post by markbuntu on 2008-12-03
For some cards, having the spdif enabled disables the rest of the sound. You may need to add an option to the snd_hda_intel module. I am on Mandriva at the moment and have no access to my notes but try a search in the forums.

---

### Post by theirishfozz on 2008-12-07
I've given up on alsa again and went back to OSS. I put the alsa modules back into the blacklist, installed oss and it worked right away. So much easier.

thanks guys

---

