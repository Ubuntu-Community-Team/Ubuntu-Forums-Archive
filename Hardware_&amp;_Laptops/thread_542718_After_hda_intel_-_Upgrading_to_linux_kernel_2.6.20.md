---
title: "After hda_intel - Upgrading to linux kernel 2.6.20-16 there is no sound"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by think!! on 2007-09-04
Hello, I upgradet to the new Linux kernel 2.6.20-16 but now the System doesn't find the soundcard anymore. If I look with hwinfo it is found but if I want to load it with modprobe I get the following error:
```
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
```

If I choose the kernel 2.6.20-15 at starting the sound is working fine.

thx,
think!!

---

### Post by hstenzel on 2007-09-04
I'm seeing much the same thing, I've attached relevant dmesg output.

This is a regression from previous kernel.

```

:~$ uname -a
Linux umbrage 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
$ dmesg | grep snd
[   18.448000] snd_rawmidi: Unknown symbol snd_register_device
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   18.516000] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   18.720000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[   18.720000] snd_hda_codec: Unknown symbol snd_ctl_add
[   18.720000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[   18.720000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[   18.720000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[   18.720000] snd_hda_codec: Unknown symbol snd_ctl_new1
[   18.720000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[   18.720000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[   18.720000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.720000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[   18.720000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   18.720000] snd_hda_intel: Unknown symbol snd_pcm_new
[   18.720000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   18.720000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   18.720000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   18.720000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   18.720000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[   18.720000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[   18.720000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[   18.720000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[   18.720000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   18.720000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   18.724000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   18.724000] snd_hda_intel: Unknown symbol snd_hda_suspend
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   18.724000] snd_hda_intel: Unknown symbol snd_hda_resume
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   18.724000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   18.724000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.724000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

---

