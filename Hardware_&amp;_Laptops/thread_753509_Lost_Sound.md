---
title: "Lost Sound"
date: 2008-04-12
forum: Hardware &amp; Laptops
---

### Post by afderrick on 2008-04-12
So I bought a new sound card and tried to install it.  I was only getting 2.1 audio out of my 5.1 system so I decided to go back to the old setup and just use the onboard sound.  I was only having one problem and I decided I could live with it.  I removed the sound card, setup my bios to use onboard sound again, but when I get into Ubuntu I am not getting any sound.  It tells me no devices found.  I ran a dmesg to try and figure out what the problem is, but it's all greek to me.  Does anyone have any suggestions?

Below is the dmesg output that I believe relates to sound.

[PHP][   32.630440] input: PC Speaker as /class/input/input2
[   32.689250] snd_hda_intel: Unknown symbol snd_ctl_add
[   32.689296] snd_hda_intel: Unknown symbol snd_pcm_new
[   32.689338] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   32.689374] snd_hda_intel: Unknown symbol snd_card_register
[   32.689406] snd_hda_intel: Unknown symbol snd_card_free
[   32.689437] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   32.689469] snd_hda_intel: Unknown symbol snd_card_proc_new
[   32.689578] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   32.689622] snd_hda_intel: Unknown symbol snd_dma_free_pages
[   32.689654] snd_hda_intel: Unknown symbol snd_ctl_new1
[   32.689722] snd_hda_intel: Unknown symbol snd_component_add
[   32.689772] snd_hda_intel: Unknown symbol snd_card_new
[   32.689804] snd_hda_intel: Unknown symbol snd_iprintf
[   32.689840] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   32.689883] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   32.689919] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   32.689951] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   32.689998] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   32.690030] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   32.690072] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   32.690114] snd_hda_intel: Unknown symbol snd_device_new
[   32.690163] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   32.690200] snd_hda_intel: Unknown symbol snd_card_disconnect
[   32.690231] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   32.690310] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   32.690358] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[   32.690390] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   32.690422] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   32.690477] snd_hda_intel: Unknown symbol snd_pcm_format_width
[/PHP]

---

### Post by afderrick on 2008-04-12
still trying to find a resolution, if I try to run alsamixer the error I get is:

alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference


Can anyone help? or do I need to get ready to back up all my data?

---

### Post by afderrick on 2008-04-12
Alright, still been working on it. an update.

According to [www.alsa-project.org](www.alsa-project.org) my sound card (Razer Barracuda AC-1) is supported, but if I type in sudo modprobe snd- and then hit <tab> I do not get the chipset that is listed at Alsa Project of CMI8788.  I have no clue what to do, please someone help.

---

