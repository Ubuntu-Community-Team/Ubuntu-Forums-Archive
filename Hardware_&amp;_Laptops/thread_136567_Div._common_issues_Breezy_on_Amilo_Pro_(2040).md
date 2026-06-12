---
title: "Div. common issues: Breezy on Amilo Pro (2040)"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by Hellkeepa on 2006-02-26
HELLo!

I have just recently purchased a Fujitsu-Siemens Amilo Pro 2040, and promplty installed Linux on it (Ubuntu 5.10, obviously). The installation was pretty much straight-forward, except for a few minor issues. So I thought it would be a good idea to start a thread dedicated to this laptop, and some of the common issues experienced with it.

Some of the issues I've been able to fix already, using the following posts. (**Please note that "build-essentials" are needed for some of these fixes.**)
[WiFi led](http://ubuntuforums.org/showpost.php?p=545771&postcount=26)
[Sound fixes](http://ubuntuforums.org/showpost.php?p=725853&postcount=127)
[Automatix](http://ubuntuforums.org/showthread.php?t=66563) (codecs and so forth)

There are, however some more issues that I haven't been able to find a solution for:
[list]
[*]Not being able to control volume with Fn+F5 trough Fn+F7.
The rather puzzling part is that I get the Gnome volume splash-screen, the speaker with the volume-bar beneath (showing full volume, even if this isn't the case). It doesn't matter which of the three combinations I push, the bar doesn't budge and nothing else happens.
So I was hoping someone here could point me to which files I have to edit, and what the correct values are, to get this to work? I'm aware that I can use [xbindkeys](http://ubuntuforums.org/showpost.php?p=572079&postcount=4) for this, but that looks too much like circumventing the problem for my taste; The buttons are working, and sending signals to some volume-related application after all.
[*]No HDD LED when HDD is working.
This one I've not been able to find anything on, not even with a google-search, so I'm completely clueless on this one. Any suggestions on how to get my HDD LED working would be much appreciated; It's completely dead.
[/list]

Also, here's some other threads that some people might find useful:
[Disabling/configuring touchpad](http://ubuntuforums.org/showthread.php?t=134865)
[Decreasing overall font size](http://ubuntuforums.org/showthread.php?t=125421&page=2) (more space on screen)

One thing there seems to be no fix for yet is the card-reader, as there are no drivers to be found (from what I was able to discern).

If there are anyone else with problems, please post them up in here with as much details as possible, so that it'll be easier for those who're trying to help you. ;-)

For those of you who would like to help, I ask that you please be so kind as to explain things in such a simple manner as possible. This to ensure that as many people as possible will be able to follow your instructions, and the maximum "value" of this thread for later reference. ;)

Happy thinkerin'!

---

### Post by Hellkeepa on 2006-02-27
HELLo!

Changed the title and bumping this one, as it's only 2 people except me who's looked at the thread since I posted it.. :(

Happy thinkerin'!

---

### Post by Hellkeepa on 2006-03-14
HELLo!

Seriously, no-one that has any ideas on my questions?

I also got a new problem, with the kernel update yesterday: My sound went missing. This is the output from "dmsg | grep snd"
> [4294707.526000] snd_timer: Unknown symbol snd_info_free_entry
[4294707.526000] snd_timer: disagrees about version of symbol snd_unregister_device
[4294707.526000] snd_timer: Unknown symbol snd_unregister_device
[4294707.526000] snd_timer: disagrees about version of symbol snd_device_new
[4294707.526000] snd_timer: Unknown symbol snd_device_new
[4294707.526000] snd_timer: Unknown symbol snd_kmalloc_strdup
[4294707.526000] snd_timer: disagrees about version of symbol snd_info_unregister
[4294707.526000] snd_timer: Unknown symbol snd_info_unregister
[4294707.526000] snd_timer: disagrees about version of symbol snd_register_device
[4294707.526000] snd_timer: Unknown symbol snd_register_device
[4294707.526000] snd_pcm: Unknown symbol snd_timer_notify
[4294707.526000] snd_pcm: Unknown symbol snd_timer_interrupt
[4294707.527000] snd_pcm: disagrees about version of symbol snd_malloc_pages
[4294707.527000] snd_pcm: Unknown symbol snd_malloc_pages
[4294707.527000] snd_pcm: Unknown symbol snd_timer_new
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[4294707.528000] snd_hda_codec: Unknown symbol snd_ctl_add
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[4294707.528000] snd_hda_codec: Unknown symbol snd_card_proc_new
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[4294707.528000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[4294707.528000] snd_hda_codec: Unknown symbol snd_ctl_new1
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_component_add
[4294707.528000] snd_hda_codec: Unknown symbol snd_component_add
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[4294707.528000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[4294707.528000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[4294707.528000] snd_hda_codec: disagrees about version of symbol snd_device_new
[4294707.528000] snd_hda_codec: Unknown symbol snd_device_new
[4294707.528000] snd_hda_codec: Unknown symbol snd_kmalloc_strdup
[4294707.528000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[4294707.528000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[4294707.542000] snd_timer: disagrees about version of symbol snd_info_register
[4294707.542000] snd_timer: Unknown symbol snd_info_register
[4294707.542000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[4294707.542000] snd_timer: Unknown symbol snd_info_create_module_entry
[4294707.542000] snd_timer: disagrees about version of symbol snd_info_free_entry
[4294707.542000] snd_timer: Unknown symbol snd_info_free_entry
[4294707.542000] snd_timer: disagrees about version of symbol snd_unregister_device
[4294707.542000] snd_timer: Unknown symbol snd_unregister_device
[4294707.542000] snd_timer: disagrees about version of symbol snd_device_new
[4294707.542000] snd_timer: Unknown symbol snd_device_new
[4294707.542000] snd_timer: Unknown symbol snd_kmalloc_strdup
[4294707.542000] snd_timer: disagrees about version of symbol snd_info_unregister
[4294707.542000] snd_timer: Unknown symbol snd_info_unregister
[4294707.542000] snd_timer: disagrees about version of symbol snd_register_device
[4294707.542000] snd_timer: Unknown symbol snd_register_device
[4294707.553000] snd_timer: disagrees about version of symbol snd_info_register
[4294707.553000] snd_timer: Unknown symbol snd_info_register
[4294707.553000] snd_timer: disagrees about version of symbol snd_info_create_module_entry
[4294707.553000] snd_timer: Unknown symbol snd_info_create_module_entry
[4294707.553000] snd_timer: disagrees about version of symbol snd_info_free_entry
[4294707.553000] snd_timer: Unknown symbol snd_info_free_entry
[4294707.553000] snd_timer: disagrees about version of symbol snd_unregister_device
[4294707.553000] snd_timer: Unknown symbol snd_unregister_device
[4294707.553000] snd_timer: disagrees about version of symbol snd_device_new
[4294707.553000] snd_timer: Unknown symbol snd_device_new
[4294707.553000] snd_timer: Unknown symbol snd_kmalloc_strdup
[4294707.553000] snd_timer: disagrees about version of symbol snd_info_unregister
[4294707.553000] snd_timer: Unknown symbol snd_info_unregister
[4294707.553000] snd_timer: disagrees about version of symbol snd_register_device
[4294707.553000] snd_timer: Unknown symbol snd_register_device
[4294707.554000] snd_pcm: Unknown symbol snd_timer_notify
[4294707.554000] snd_pcm: Unknown symbol snd_timer_interrupt
[4294707.554000] snd_pcm: disagrees about version of symbol snd_malloc_pages
[4294707.554000] snd_pcm: Unknown symbol snd_malloc_pages
[4294707.554000] snd_pcm: Unknown symbol snd_timer_new
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[4294707.555000] snd_hda_codec: Unknown symbol snd_ctl_add
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[4294707.555000] snd_hda_codec: Unknown symbol snd_card_proc_new
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[4294707.555000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[4294707.555000] snd_hda_codec: Unknown symbol snd_ctl_new1
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_component_add
[4294707.555000] snd_hda_codec: Unknown symbol snd_component_add
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[4294707.555000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[4294707.555000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[4294707.555000] snd_hda_codec: disagrees about version of symbol snd_device_new
[4294707.556000] snd_hda_codec: Unknown symbol snd_device_new
[4294707.556000] snd_hda_codec: Unknown symbol snd_kmalloc_strdup
[4294707.556000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[4294707.556000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[4294707.556000] snd_hda_intel: Unknown symbol snd_pcm_new
[4294707.556000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[4294707.556000] snd_hda_intel: disagrees about version of symbol snd_card_register
[4294707.556000] snd_hda_intel: Unknown symbol snd_card_register
[4294707.556000] snd_hda_intel: disagrees about version of symbol snd_card_free
[4294707.556000] snd_hda_intel: Unknown symbol snd_card_free
[4294707.556000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4294707.556000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[4294707.556000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[4294707.556000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[4294707.556000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[4294707.556000] snd_hda_intel: disagrees about version of symbol snd_card_new
[4294707.556000] snd_hda_intel: Unknown symbol snd_card_new
[4294707.556000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[4294707.556000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[4294707.557000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[4294707.557000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[4294707.557000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[4294707.557000] snd_hda_intel: disagrees about version of symbol snd_card_set_pm_callback
[4294707.557000] snd_hda_intel: Unknown symbol snd_card_set_pm_callback
[4294707.557000] snd_hda_intel: Unknown symbol snd_hda_suspend
[4294707.557000] snd_hda_intel: disagrees about version of symbol snd_device_new
[4294707.557000] snd_hda_intel: Unknown symbol snd_device_new
[4294707.557000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[4294707.557000] snd_hda_intel: Unknown symbol snd_hda_resume
[4294707.557000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[4294707.557000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[4294707.557000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed

Are there someone out there who could be kind enough to help me on this?

Happy codin'!

---

