---
title: "Strange sound problem (AC97) + partial solution?"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by Smalle2000 on 2005-05-27
Hi,

As a lot of ubuntu users with an onboard sound card I had a lot of problems to get my sound working. I tried all the instructions (unofficial ubuntu guide, Howto: About sound in Hoary & Linux and Hoary sound broke), but couldn't get it to work. I kept receiving the same errors as a lot of people - being able to hear te intro with the loginscreen, but 'constructing pipeline' error,... . Then I realised when I did 'sudo killall esd' I got the response 'esd: no process killed'. So I tried to do 'sudo esd' and suddenly my sound was working! So this might be a partial solution for some people (maybe a good idea to put it in the howto?).

But now I can't resolve the problem anymore with the 'sudo esd'-command. It returns: ```
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
``` 

Trying to open alsamixer (sudo alsamixer) gives: ```
alsamixer: function snd_ctl_open failed for default: No such device
``` 

My sound card is from the following type:
SiS Si7012
Realtek ALC650E

I'll give some more returns to some commands, hopefully somebody can see the reason of the sudden stop in sound:

lsof /def/dsp:```
lsof: status error on /dev/dsp: No such file or directory
``` 

lsmod|grep snd:```
snd_timer              23300  0
snd_page_alloc          9604  0
snd_mixer_oss          16768  0
snd                    50276  2 snd_timer,snd_mixer_oss
soundcore               9824  2 saa7134,snd
``` 
There used to be snd_intel8x0 etc.

sudo strace -eopen alsamixer: ```
open("/etc/ld.so.preload", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/etc/asound.conf", O_RDONLY)      = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENODEV (No such device)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC0", O_RDWR)      = -1 ENODEV (No such device)
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENODEV (No such device)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)
open("/dev/snd/controlC0", O_RDWR)      = -1 ENODEV (No such device)
``` 

sudo ls -l /dev/snd/controlC0: ```
crw-rw----  1 root audio 116, 0 2005-05-27 11:54 /dev/snd/controlC0
``` 

And what I thinks is the relevant code from 'dmesg': ```
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: disagrees about version of symbol snd_device_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: disagrees about version of symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: disagrees about version of symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: disagrees about version of symbol snd_power_wait
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_hidden_kmalloc
snd_pcm: disagrees about version of symbol snd_device_free
snd_pcm: Unknown symbol snd_device_free
snd_pcm: disagrees about version of symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: disagrees about version of symbol snd_info_unregister
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: disagrees about version of symbol snd_device_register
snd_pcm: Unknown symbol snd_device_register
snd_pcm: disagrees about version of symbol snd_register_device
snd_pcm: Unknown symbol snd_register_device
snd_ac97_codec: disagrees about version of symbol snd_info_register
snd_ac97_codec: Unknown symbol snd_info_register
snd_ac97_codec: disagrees about version of symbol snd_ctl_add
snd_ac97_codec: Unknown symbol snd_ctl_add
snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
snd_ac97_codec: Unknown symbol snd_info_free_entry
snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
snd_ac97_codec: Unknown symbol snd_interval_refine
snd_ac97_codec: Unknown symbol snd_hidden_kfree
snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
snd_ac97_codec: Unknown symbol snd_ctl_find_id
snd_ac97_codec: Unknown symbol snd_verbose_printk
snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
snd_ac97_codec: Unknown symbol snd_ctl_new1
snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
snd_ac97_codec: Unknown symbol snd_ctl_remove_id
snd_ac97_codec: disagrees about version of symbol snd_component_add
snd_ac97_codec: Unknown symbol snd_component_add
snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
snd_ac97_codec: disagrees about version of symbol snd_device_new
snd_ac97_codec: Unknown symbol snd_device_new
snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
snd_ac97_codec: Unknown symbol snd_info_create_card_entry
snd_ac97_codec: disagrees about version of symbol snd_info_unregister
snd_ac97_codec: Unknown symbol snd_info_unregister
snd_pcm: Unknown symbol snd_verbose_printd
snd_pcm: disagrees about version of symbol snd_info_register
snd_pcm: Unknown symbol snd_info_register
snd_pcm: disagrees about version of symbol snd_info_create_module_entry
snd_pcm: Unknown symbol snd_info_create_module_entry
snd_pcm: disagrees about version of symbol snd_timer_notify
snd_pcm: Unknown symbol snd_timer_notify
snd_pcm: disagrees about version of symbol snd_timer_interrupt
snd_pcm: Unknown symbol snd_timer_interrupt
snd_pcm: disagrees about version of symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_hidden_kcalloc
snd_pcm: Unknown symbol snd_hidden_kfree
snd_pcm: Unknown symbol snd_verbose_printk
snd_pcm: disagrees about version of symbol snd_ctl_register_ioctl
snd_pcm: Unknown symbol snd_ctl_register_ioctl
snd_pcm: disagrees about version of symbol snd_card_file_add
snd_pcm: Unknown symbol snd_card_file_add
snd_pcm: disagrees about version of symbol snd_unregister_device
snd_pcm: Unknown symbol snd_unregister_device
snd_pcm: disagrees about version of symbol snd_timer_new
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: disagrees about version of symbol snd_device_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: disagrees about version of symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: disagrees about version of symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: disagrees about version of symbol snd_power_wait
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_hidden_kmalloc
snd_pcm: disagrees about version of symbol snd_device_free
snd_pcm: Unknown symbol snd_device_free
snd_pcm: disagrees about version of symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: disagrees about version of symbol snd_info_unregister
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: disagrees about version of symbol snd_device_register
snd_pcm: Unknown symbol snd_device_register
snd_pcm: disagrees about version of symbol snd_register_device
snd_pcm: Unknown symbol snd_register_device
snd_ac97_codec: disagrees about version of symbol snd_info_register
snd_ac97_codec: Unknown symbol snd_info_register
snd_ac97_codec: disagrees about version of symbol snd_ctl_add
snd_ac97_codec: Unknown symbol snd_ctl_add
snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
snd_ac97_codec: Unknown symbol snd_info_free_entry
snd_ac97_codec: Unknown symbol snd_hidden_kcalloc
snd_ac97_codec: Unknown symbol snd_interval_refine
snd_ac97_codec: Unknown symbol snd_hidden_kfree
snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
snd_ac97_codec: Unknown symbol snd_ctl_find_id
snd_ac97_codec: Unknown symbol snd_verbose_printk
snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
snd_ac97_codec: Unknown symbol snd_ctl_new1
snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
snd_ac97_codec: Unknown symbol snd_ctl_remove_id
snd_ac97_codec: disagrees about version of symbol snd_component_add
snd_ac97_codec: Unknown symbol snd_component_add
snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
snd_ac97_codec: disagrees about version of symbol snd_device_new
snd_ac97_codec: Unknown symbol snd_device_new
snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
snd_ac97_codec: Unknown symbol snd_info_create_card_entry
snd_ac97_codec: disagrees about version of symbol snd_info_unregister
snd_ac97_codec: Unknown symbol snd_info_unregister
snd_intel8x0: Unknown symbol snd_verbose_printd
snd_intel8x0: Unknown symbol snd_ac97_pcm_close
snd_intel8x0: Unknown symbol snd_ac97_resume
snd_intel8x0: Unknown symbol snd_pcm_new
snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
snd_intel8x0: disagrees about version of symbol snd_card_register
snd_intel8x0: Unknown symbol snd_card_register
snd_intel8x0: disagrees about version of symbol snd_card_free
snd_intel8x0: Unknown symbol snd_card_free
snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
snd_intel8x0: disagrees about version of symbol snd_card_proc_new
snd_intel8x0: Unknown symbol snd_card_proc_new
snd_intel8x0: Unknown symbol snd_ac97_pcm_open
snd_intel8x0: Unknown symbol snd_hidden_kcalloc
snd_intel8x0: Unknown symbol snd_ac97_set_rate
snd_intel8x0: Unknown symbol snd_ac97_update_bits
snd_intel8x0: Unknown symbol snd_hidden_kfree
snd_intel8x0: Unknown symbol snd_ac97_mixer
snd_intel8x0: Unknown symbol snd_ac97_bus
snd_intel8x0: Unknown symbol snd_verbose_printk
snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
snd_intel8x0: disagrees about version of symbol snd_card_new
snd_intel8x0: Unknown symbol snd_card_new
snd_intel8x0: Unknown symbol snd_ac97_suspend
snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
snd_intel8x0: Unknown symbol snd_pcm_set_ops
snd_intel8x0: disagrees about version of symbol snd_card_set_pm_callback
snd_intel8x0: Unknown symbol snd_card_set_pm_callback
snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
snd_intel8x0: disagrees about version of symbol snd_device_new
snd_intel8x0: Unknown symbol snd_device_new
snd_intel8x0: Unknown symbol snd_ac97_get_short_name
snd_intel8x0: Unknown symbol snd_pcm_suspend_all
snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
snd_intel8x0: Unknown symbol snd_ac97_tune_hardware
``` 

Is there anybody who can help me with this problem? I really don't understand how it can suddenly stop working, while I don't remember to have changed anything to my system since it last worked.

Thanks in advance (and my excuses for my not-too-good knowledge of English),
  Stijn

---

