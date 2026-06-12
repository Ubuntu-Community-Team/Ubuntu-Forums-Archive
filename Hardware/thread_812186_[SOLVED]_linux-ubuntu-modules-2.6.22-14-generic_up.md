---
title: "[SOLVED] linux-ubuntu-modules-2.6.22-14-generic update killed ALSA"
date: 2008-05-29
forum: Hardware
---

### Post by blumf on 2008-05-29
Gutsy 7.10

The update of the linux-ubuntu-modules-2.6.22-14-generic package on the 27th messed up my ALSA modules.

A bit of background:
I had to update the ALSA drivers to the latest version (1.0.16) using [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") guide to get my sound card working properly. The process went smoothly and my sound card worked correctly afterwards.

Now, since the linux-ubuntu-modules update the ALSA modules do not work. I tried rebuilding them from clean sources (and the timestamps on the .ko files in /lib/modules/... show they have been updated).

The relevant messages from dmesg:
```
[   14.276000] snd: Unknown symbol unregister_sound_special
[   14.276000] snd: Unknown symbol register_sound_special_device
[   14.276000] snd: Unknown symbol sound_class
[   14.296000] snd_timer: Unknown symbol snd_info_register
[   14.296000] snd_timer: Unknown symbol snd_info_create_module_entry
[   14.296000] snd_timer: Unknown symbol snd_info_free_entry
[   14.296000] snd_timer: Unknown symbol snd_verbose_printk
[   14.296000] snd_timer: Unknown symbol snd_iprintf
[   14.296000] snd_timer: Unknown symbol snd_ecards_limit
[   14.296000] snd_timer: Unknown symbol snd_oss_info_register
[   14.296000] snd_timer: Unknown symbol snd_unregister_device
[   14.296000] snd_timer: Unknown symbol snd_device_new
[   14.296000] snd_timer: Unknown symbol snd_register_device_for_dev
[   14.320000] snd: Unknown symbol unregister_sound_special
[   14.320000] snd: Unknown symbol register_sound_special_device
[   14.324000] snd: Unknown symbol sound_class
[   14.416000] snd_timer: Unknown symbol snd_info_register
[   14.416000] snd_timer: Unknown symbol snd_info_create_module_entry
[   14.416000] snd_timer: Unknown symbol snd_info_free_entry
[   14.416000] snd_timer: Unknown symbol snd_verbose_printk
[   14.416000] snd_timer: Unknown symbol snd_iprintf
[   14.416000] snd_timer: Unknown symbol snd_ecards_limit
[   14.416000] snd_timer: Unknown symbol snd_oss_info_register
[   14.416000] snd_timer: Unknown symbol snd_unregister_device
[   14.416000] snd_timer: Unknown symbol snd_device_new
[   14.416000] snd_timer: Unknown symbol snd_register_device_for_dev
[   14.484000] snd_pcm: Unknown symbol snd_info_register
[   14.484000] snd_pcm: Unknown symbol snd_info_create_module_entry
[   14.484000] snd_pcm: Unknown symbol snd_timer_notify
[   14.484000] snd_pcm: Unknown symbol snd_timer_interrupt
[   14.484000] snd_pcm: Unknown symbol snd_info_free_entry
[   14.484000] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[   14.484000] snd_pcm: Unknown symbol snd_info_get_str
[   14.484000] snd_pcm: Unknown symbol snd_verbose_printk
[   14.484000] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[   14.484000] snd_pcm: Unknown symbol snd_card_file_add
[   14.484000] snd_pcm: Unknown symbol snd_iprintf
[   14.484000] snd_pcm: Unknown symbol snd_major
[   14.484000] snd_pcm: Unknown symbol snd_unregister_device
[   14.484000] snd_pcm: Unknown symbol snd_timer_new
[   14.484000] snd_pcm: Unknown symbol snd_device_new
[   14.484000] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[   14.484000] snd_pcm: Unknown symbol snd_lookup_minor_data
[   14.484000] snd_pcm: Unknown symbol snd_info_create_card_entry
[   14.484000] snd_pcm: Unknown symbol snd_power_wait
[   14.484000] snd_pcm: Unknown symbol snd_device_free
[   14.484000] snd_pcm: Unknown symbol snd_card_file_remove
[   14.484000] snd_pcm: Unknown symbol snd_register_device_for_dev
[   14.484000] snd_pcm: Unknown symbol snd_device_register
[   14.484000] snd_pcm: Unknown symbol snd_info_get_line
[   14.600000] snd_hda_intel: Unknown symbol snd_ctl_add
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_new
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   14.600000] snd_hda_intel: Unknown symbol snd_card_register
[   14.600000] snd_hda_intel: Unknown symbol snd_card_free
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   14.600000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   14.600000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   14.600000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   14.600000] snd_hda_intel: Unknown symbol snd_component_add
[   14.600000] snd_hda_intel: Unknown symbol snd_card_new
[   14.600000] snd_hda_intel: Unknown symbol snd_iprintf
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   14.600000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   14.600000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   14.600000] snd_hda_intel: Unknown symbol snd_device_new
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   14.600000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   14.600000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   14.604000] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   14.604000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   14.604000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   14.604000] snd_hda_intel: Unknown symbol snd_pcm_format_width

```

Any idea what changed to break this?

---

### Post by bissej on 2008-05-30
Hi.
I'm having a similar, or at least related, problem. I'm also running 7.10 (i'm on a AMD 64). I did the recent update, and then when I turned my computer on the next day, it booted in some strange Gnome safe mode. WHen I try to shut down, it freezes on "shutting down ALSA". Any idea what to do?

thanks.

---

### Post by blumf on 2008-05-30
After some digging around I noticed that soundcore.ko was missing, think I might have lost that myself :oops:

[LIST=1]
[*]Reinstall of the linux-image-2.6.22-14-generic package
[*]'make install' of the ALSA drivers package
[*]Replaced /lib/modules/.../ubuntu/media/snd-hda-intel/snd-hda-intel.ko with the new ALSA one in .../kernel/sound/pci/hda/snd-hda-intel.ko
[*]'depmod -a'
[*]Reboot
[/LIST]

Fixed it.

---

