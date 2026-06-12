---
title: "coundnot use ALSA on FC5test1,help!"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by ddd999 on 2006-01-06
may FC5T1 original  ALSA,may soundcard in envy1724
[root@localhost ~]# rpm -qa |grep alsa
alsa-lib-devel-1.0.10rc1-2
alsa-utils-1.0.10rc1-2
alsa-lib-1.0.10rc1-2
I update to alsa-1.0.11rc2 because I cannot find Audigy Analog/Digital Output Jack in alsamixer
I install the 4 
alsa-driver-1.0.11rc2,alsa-lib-1.0.11rc2,alsa-utils-1.0.11rc2,alsa-oss-1.0.10
ALSA cannot work

---

### Post by ddd999 on 2006-01-06
alsaconf
.....................................
Loading driver...
Starting sound driver: snd-ice1724 WARNING: Error inserting snd (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ak4114 (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/i2c/other/snd-ak4114.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1724 (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ice1712/snd-ice1724.ko): Unknown symbol in module, or unknown parameter (see dmesg)
done
Starting sound driver: snd-mpu401 WARNING: Error inserting snd (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_mpu401 (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/drivers/mpu401/snd-mpu401.ko): Unknown symbol in module, or unknown parameter (see dmesg)
done
Starting sound driver: snd-ice1724 WARNING: Error inserting snd (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ak4114 (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/i2c/other/snd-ak4114.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1724 (/lib/modules/2.6.14-1.1696_FC5/kernel/sound/pci/ice1712/snd-ice1724.ko): Unknown symbol in module, or unknown parameter (see dmesg)
done
Setting default volumes...
amixer: Mixer attach default error: No such device

---

### Post by ddd999 on 2006-01-06
dmesg:part
..........
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_init
snd_ice1724: Unknown symbol snd_ac97_write_cache
snd_ice1724: Unknown symbol snd_ctl_add
snd_ice1724: Unknown symbol snd_pcm_new
snd_ice1724: Unknown symbol snd_card_register
snd_ice1724: Unknown symbol snd_card_free
snd_ice1724: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
snd_ice1724: Unknown symbol snd_card_proc_new
snd_ice1724: Unknown symbol snd_ac97_mixer
snd_ice1724: Unknown symbol snd_ak4114_create
snd_ice1724: Unknown symbol snd_ac97_bus
snd_ice1724: Unknown symbol snd_pcm_set_sync
snd_ice1724: Unknown symbol snd_verbose_printk
snd_ice1724: Unknown symbol snd_ctl_new1
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_free
snd_ice1724: Unknown symbol snd_card_new
snd_ice1724: Unknown symbol snd_iprintf
snd_ice1724: Unknown symbol snd_pcm_lib_malloc_pages
snd_ice1724: Unknown symbol snd_pcm_lib_ioctl
snd_ice1724: Unknown symbol snd_pcm_lib_free_pages
snd_ice1724: Unknown symbol snd_akm4xxx_reset
snd_ice1724: Unknown symbol snd_pcm_set_ops
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_list
snd_ice1724: Unknown symbol snd_device_new
snd_ice1724: Unknown symbol snd_mpu401_uart_interrupt
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_build_controls
snd_ice1724: Unknown symbol snd_mpu401_uart_new
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_msbits
snd_ice1724: Unknown symbol snd_pcm_period_elapsed
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_step
snd_ice1724: Unknown symbol snd_ac97_read
snd_ice1724: Unknown symbol snd_info_get_line
snd: Unknown symbol pm_register
snd: Unknown symbol pm_unregister
snd_seq_device: Unknown symbol snd_info_register
snd_seq_device: Unknown symbol snd_info_create_module_entry
snd_seq_device: Unknown symbol snd_info_free_entry
snd_seq_device: Unknown symbol snd_seq_root
snd_seq_device: Unknown symbol snd_verbose_printk
snd_seq_device: Unknown symbol snd_iprintf
snd_seq_device: Unknown symbol snd_device_new
snd_seq_device: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_info_register
snd_rawmidi: Unknown symbol snd_seq_device_new
snd_rawmidi: Unknown symbol snd_info_free_entry
snd_rawmidi: Unknown symbol snd_unregister_oss_device
snd_rawmidi: Unknown symbol snd_verbose_printk
snd_rawmidi: Unknown symbol snd_register_oss_device
snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
snd_rawmidi: Unknown symbol snd_card_file_add
snd_rawmidi: Unknown symbol snd_iprintf
snd_rawmidi: Unknown symbol snd_major
snd_rawmidi: Unknown symbol snd_oss_info_register
snd_rawmidi: Unknown symbol snd_unregister_device
snd_rawmidi: Unknown symbol snd_device_new
snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
snd_rawmidi: Unknown symbol snd_lookup_minor_data
snd_rawmidi: Unknown symbol snd_info_create_card_entry
snd_rawmidi: Unknown symbol snd_device_free
snd_rawmidi: Unknown symbol snd_card_file_remove
snd_rawmidi: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_device_register
snd_rawmidi: Unknown symbol snd_register_device
snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
snd_mpu401_uart: Unknown symbol snd_verbose_printk
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
snd_mpu401_uart: Unknown symbol release_and_free_resource
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
snd_mpu401_uart: Unknown symbol snd_rawmidi_new
snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
snd_mpu401_uart: Unknown symbol snd_device_free
snd_mpu401: Unknown symbol snd_card_register
snd_mpu401: Unknown symbol snd_card_free
snd_mpu401: Unknown symbol snd_verbose_printk
snd_mpu401: Unknown symbol snd_pnp_register_driver
snd_mpu401: Unknown symbol snd_card_new
snd_mpu401: Unknown symbol snd_card_disconnect
snd_mpu401: Unknown symbol snd_mpu401_uart_new
snd_mpu401: Unknown symbol snd_card_free_in_thread
snd: Unknown symbol pm_register
snd: Unknown symbol pm_unregister
snd_seq_device: Unknown symbol snd_info_register
snd_seq_device: Unknown symbol snd_info_create_module_entry
snd_seq_device: Unknown symbol snd_info_free_entry
snd_seq_device: Unknown symbol snd_seq_root
snd_seq_device: Unknown symbol snd_verbose_printk
snd_seq_device: Unknown symbol snd_iprintf
snd_seq_device: Unknown symbol snd_device_new
snd_seq_device: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_info_register
snd_rawmidi: Unknown symbol snd_seq_device_new
snd_rawmidi: Unknown symbol snd_info_free_entry
snd_rawmidi: Unknown symbol snd_unregister_oss_device
snd_rawmidi: Unknown symbol snd_verbose_printk
snd_rawmidi: Unknown symbol snd_register_oss_device
snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
snd_rawmidi: Unknown symbol snd_card_file_add
snd_rawmidi: Unknown symbol snd_iprintf
snd_rawmidi: Unknown symbol snd_major
snd_rawmidi: Unknown symbol snd_oss_info_register
snd_rawmidi: Unknown symbol snd_unregister_device
snd_rawmidi: Unknown symbol snd_device_new
snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
snd_rawmidi: Unknown symbol snd_lookup_oss_minor_data
snd_rawmidi: Unknown symbol snd_lookup_minor_data
snd_rawmidi: Unknown symbol snd_info_create_card_entry
snd_rawmidi: Unknown symbol snd_device_free
snd_rawmidi: Unknown symbol snd_card_file_remove
snd_rawmidi: Unknown symbol snd_info_unregister
snd_rawmidi: Unknown symbol snd_device_register
snd_rawmidi: Unknown symbol snd_register_device
snd_mpu401_uart: Unknown symbol snd_rawmidi_receive
snd_mpu401_uart: Unknown symbol snd_verbose_printk
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_ack
snd_mpu401_uart: Unknown symbol release_and_free_resource
snd_mpu401_uart: Unknown symbol snd_rawmidi_transmit_peek
snd_mpu401_uart: Unknown symbol snd_rawmidi_new
snd_mpu401_uart: Unknown symbol snd_rawmidi_set_ops
snd_mpu401_uart: Unknown symbol snd_device_free
snd_ak4xxx_adda: Unknown symbol snd_ctl_add
snd_ak4xxx_adda: Unknown symbol snd_ctl_new
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_verbose_printk
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd: Unknown symbol pm_register
snd: Unknown symbol pm_unregister
snd_timer: Unknown symbol snd_info_register
snd_timer: Unknown symbol snd_info_create_module_entry
snd_timer: Unknown symbol snd_info_free_entry
snd_timer: Unknown symbol snd_verbose_printk
snd_timer: Unknown symbol snd_iprintf
snd_timer: Unknown symbol snd_ecards_limit
snd_timer: Unknown symbol snd_oss_info_register
snd_timer: Unknown symbol snd_unregister_device
snd_timer: Unknown symbol snd_device_new
snd_timer: Unknown symbol snd_info_unregister
snd_timer: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_register
snd_pcm: Unknown symbol snd_info_create_module_entry
snd_pcm: Unknown symbol snd_timer_notify
snd_pcm: Unknown symbol snd_timer_interrupt
snd_pcm: Unknown symbol snd_info_free_entry
snd_pcm: Unknown symbol snd_info_get_str
snd_pcm: Unknown symbol snd_verbose_printk
snd_pcm: Unknown symbol snd_ctl_register_ioctl
snd_pcm: Unknown symbol snd_card_file_add
snd_pcm: Unknown symbol snd_iprintf
snd_pcm: Unknown symbol snd_major
snd_pcm: Unknown symbol snd_unregister_device
snd_pcm: Unknown symbol snd_timer_new
snd_pcm: Unknown symbol snd_device_new
snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
snd_pcm: Unknown symbol snd_lookup_minor_data
snd_pcm: Unknown symbol snd_info_create_card_entry
snd_pcm: Unknown symbol snd_power_wait
snd_pcm: Unknown symbol snd_device_free
snd_pcm: Unknown symbol snd_card_file_remove
snd_pcm: Unknown symbol snd_info_unregister
snd_pcm: Unknown symbol snd_device_register
snd_pcm: Unknown symbol snd_register_device
snd_pcm: Unknown symbol snd_info_get_line
snd_ak4114: Unknown symbol snd_ctl_add
snd_ak4114: Unknown symbol snd_pcm_stop
snd_ak4114: Unknown symbol snd_ctl_free_one
snd_ak4114: Unknown symbol snd_ctl_new1
snd_ak4114: Unknown symbol snd_ctl_notify
snd_ak4114: Unknown symbol snd_device_new
snd_ak4114: Unknown symbol snd_pcm_link_rwlock
snd_ac97_codec: Unknown symbol snd_info_register
snd_ac97_codec: Unknown symbol snd_ctl_add
snd_ac97_codec: Unknown symbol snd_info_free_entry
snd_ac97_codec: Unknown symbol snd_interval_refine
snd_ac97_codec: Unknown symbol snd_ctl_find_id
snd_ac97_codec: Unknown symbol snd_verbose_printk
snd_ac97_codec: Unknown symbol snd_ctl_new1
snd_ac97_codec: Unknown symbol snd_ctl_remove_id
snd_ac97_codec: Unknown symbol snd_component_add
snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
snd_ac97_codec: Unknown symbol snd_iprintf
snd_ac97_codec: Unknown symbol snd_device_new
snd_ac97_codec: Unknown symbol snd_info_create_card_entry
snd_ac97_codec: Unknown symbol snd_info_unregister
snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_init
snd_ice17xx_ak4xxx: Unknown symbol snd_akm4xxx_build_controls
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_init
snd_ice1724: Unknown symbol snd_ac97_write_cache
snd_ice1724: Unknown symbol snd_ctl_add
snd_ice1724: Unknown symbol snd_pcm_new
snd_ice1724: Unknown symbol snd_card_register
snd_ice1724: Unknown symbol snd_card_free
snd_ice1724: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
snd_ice1724: Unknown symbol snd_card_proc_new
snd_ice1724: Unknown symbol snd_ac97_mixer
snd_ice1724: Unknown symbol snd_ak4114_create
snd_ice1724: Unknown symbol snd_ac97_bus
snd_ice1724: Unknown symbol snd_pcm_set_sync
snd_ice1724: Unknown symbol snd_verbose_printk
snd_ice1724: Unknown symbol snd_ctl_new1
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_free
snd_ice1724: Unknown symbol snd_card_new
snd_ice1724: Unknown symbol snd_iprintf
snd_ice1724: Unknown symbol snd_pcm_lib_malloc_pages
snd_ice1724: Unknown symbol snd_pcm_lib_ioctl
snd_ice1724: Unknown symbol snd_pcm_lib_free_pages
snd_ice1724: Unknown symbol snd_akm4xxx_reset
snd_ice1724: Unknown symbol snd_pcm_set_ops
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_list
snd_ice1724: Unknown symbol snd_device_new
snd_ice1724: Unknown symbol snd_mpu401_uart_interrupt
snd_ice1724: Unknown symbol snd_ice1712_akm4xxx_build_controls
snd_ice1724: Unknown symbol snd_mpu401_uart_new
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_msbits
snd_ice1724: Unknown symbol snd_pcm_period_elapsed
snd_ice1724: Unknown symbol snd_pcm_hw_constraint_step
snd_ice1724: Unknown symbol snd_ac97_read
snd_ice1724: Unknown symbol snd_info_get_line
NET: Registered protocol family 4
NET: Registered protocol family 5
[root@localhost ~]#

---

### Post by ddd999 on 2006-01-06
[root@localhost ~]# alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

---

