---
title: "sound stopped working after recent dist-upgrade..."
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by IndieRockSteve on 2008-02-15
a recent update (about a week ago) caused the sound on my laptop to stop working, i've posted the dmesg output here.

any help would be appreciated!
> 
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_info_register
[  715.020000] snd_ac97_codec: Unknown symbol snd_info_register
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[  715.020000] snd_ac97_codec: Unknown symbol snd_ctl_add
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[  715.020000] snd_ac97_codec: Unknown symbol snd_info_free_entry
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[  715.020000] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[  715.020000] snd_ac97_codec: Unknown symbol snd_ctl_new1
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[  715.020000] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_component_add
[  715.020000] snd_ac97_codec: Unknown symbol snd_component_add
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[  715.020000] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[  715.020000] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  715.020000] snd_ac97_codec: Unknown symbol ac97_bus_type
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_device_new
[  715.020000] snd_ac97_codec: Unknown symbol snd_device_new
[  715.020000] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[  715.020000] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_pcm_close
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_resume
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_new
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_new
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_limit_hw_rates
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_limit_hw_rates
[  715.024000] snd_atiixp: disagrees about version of symbol snd_card_register
[  715.024000] snd_atiixp: Unknown symbol snd_card_register
[  715.024000] snd_atiixp: disagrees about version of symbol snd_card_free
[  715.024000] snd_atiixp: Unknown symbol snd_card_free
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  715.024000] snd_atiixp: disagrees about version of symbol snd_card_proc_new
[  715.024000] snd_atiixp: Unknown symbol snd_card_proc_new
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_pcm_open
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_stop
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_stop
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_update_bits
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_mixer
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_bus
[  715.024000] snd_atiixp: disagrees about version of symbol snd_card_new
[  715.024000] snd_atiixp: Unknown symbol snd_card_new
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_suspend
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_lib_malloc_pages
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_lib_ioctl
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_lib_ioctl
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_lib_free_pages
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_lib_free_pages
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_set_ops
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_set_ops
[  715.024000] snd_atiixp: disagrees about version of symbol snd_device_new
[  715.024000] snd_atiixp: Unknown symbol snd_device_new
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_get_short_name
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_suspend_all
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_suspend_all
[  715.024000] snd_atiixp: disagrees about version of symbol snd_card_disconnect
[  715.024000] snd_atiixp: Unknown symbol snd_card_disconnect
[  715.024000] snd_atiixp: Unknown symbol snd_ac97_pcm_assign
[  715.024000] snd_atiixp: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  715.024000] snd_atiixp: Unknown symbol snd_pcm_hw_constraint_integer
[  715.028000] snd_atiixp: disagrees about version of symbol snd_pcm_period_elapsed
[  715.028000] snd_atiixp: Unknown symbol snd_pcm_period_elapsed
[  715.028000] snd_atiixp: disagrees about version of symbol snd_pcm_hw_constraint_step
[  715.028000] snd_atiixp: Unknown symbol snd_pcm_hw_constraint_step
[  715.028000] snd_atiixp: Unknown symbol snd_ac97_tune_hardware


---

### Post by IndieRockSteve on 2008-02-16
anyone?

---

### Post by Kakihara on 2008-02-16
Upgrading to 2.6.24 kernel from hardy(fairly easy, just change /etc/apt/sources.list) solved this problem for me.
But anyway, considering such a big impact of some minor update makes upgrading to a different distribution the best solution.

Fsck ubuntu...

---

### Post by IndieRockSteve on 2008-02-16
so this is from a kernel upgrade? couldn't I just install the old kernel that was running? doesn't it keep the old kernel? and I could just choose it in GRUB?

---

### Post by Kakihara on 2008-02-16
I am not really sure, what is the cause. If you still have older kernel in grub, just try it.
The problem is most likely in the linux-ubuntu-modules package. So if you know how to downgrade it, try it.
And if nothing works, the hardy 2.6.24 kernel (along with appropriate modules), might help.

---

### Post by Kakihara on 2008-02-24
A better solution:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils fast-user-switch-applet gdm ubuntu-desktop ubuntu-minimal

---

