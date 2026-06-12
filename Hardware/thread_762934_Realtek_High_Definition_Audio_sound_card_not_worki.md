---
title: "Realtek High Definition Audio sound card not working (snd-hda-intel ALSA)"
date: 2008-04-22
forum: Hardware
---

### Post by linkmaster03 on 2008-04-22
I was following the instructions on this page to get my Realtek High Definition Audio sound card (on my Toshiba Satellite A135-S4727) on Ubuntu 7.10. (the sound has not been working ever since I installed Ubuntu, 5 days ago):

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

I got to General Step 4, compiled my driver and stuff, and was sent back to Step 4. This came up:

```
brad@brad-laptop-ubuntu:~$ sudo modprobe snd-hda-intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

And dmesg showed this:

```
[ 610.152000] snd_hda_intel: Unknown symbol snd_verbose_printd
[ 610.152000] snd_hda_intel: Unknown symbol snd_hidden_kzalloc
[ 610.152000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 610.152000] snd_hda_intel: Unknown symbol snd_ctl_add
[ 610.152000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 610.152000] snd_hda_intel: Unknown symbol snd_pcm_new
[ 610.152000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 610.152000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 610.156000] snd_hda_intel: Unknown symbol snd_card_register
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 610.156000] snd_hda_intel: Unknown symbol snd_card_free
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[ 610.156000] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 610.156000] snd_hda_intel: Unknown symbol snd_hidden_kcalloc
[ 610.156000] snd_hda_intel: Unknown symbol snd_hidden_kfree
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[ 610.156000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[ 610.156000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[ 610.156000] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_component_add
[ 610.156000] snd_hda_intel: Unknown symbol snd_component_add
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_card_new
[ 610.156000] snd_hda_intel: Unknown symbol snd_card_new
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 610.156000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[ 610.156000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 610.156000] snd_hda_intel: Unknown symbol snd_hidden_kstrdup
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_device_new
[ 610.156000] snd_hda_intel: Unknown symbol snd_device_new
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 610.156000] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[ 610.156000] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 610.156000] snd_hda_intel: Unknown symbol snd_hidden_kmalloc
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[ 610.156000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 610.156000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 610.156000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

---

### Post by linkmaster03 on 2008-04-23
Bump.

---

### Post by DantePasquale on 2008-04-23
Hi, I had a similar problem and had to set the sound card manufactur to Fujitsu. Unfortunately, I lost my blog entry when I upgraded ISPConfig, so I can't point you to the exact place I found this, but it's somewhere in those threads that you've already run across. I'll see if I can find it and post something later.

---

### Post by Chii on 2008-04-24
As annoying as it may sound, I'd recommend trying out the Live CD part of Ubuntu 8.04 that just came out today :s  As it may have fixes that 7.04 didn't. 

Also when I reboot to check if it does with mine, Ill see if I can get the link to you as I had the same issues (no sound) on my Toshiba and I had to apply a dsdt patch in order to get it to work. So I've got it all nice and bookmarked.

*edit*
Well, I'm now installing Kubuntu 8.04 and wireless, sound, ect seemed to work right out of the box. (Toshiba P100-ST9752)  However I cannot seem to figure out how to access my C:\ from within here as it says I do not have the permissions so I'll post the link later. Sorry >.<

Here you go if you still need the link for 7.04. (Though I'd really really recommend 8.04 at this point xD) [http://ubuntuforums.org/showthread.php?t=349491&page=13](http://ubuntuforums.org/showthread.php?t=349491&page=13) .  Hope it helps :)

---

