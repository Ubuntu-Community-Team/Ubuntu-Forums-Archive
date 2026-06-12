---
title: "Maudio Audiophile 192 + ALSA"
date: 2009-01-19
forum: Hardware
---

### Post by dcsollows on 2009-01-19
Hi, 

I have an M-Audio Audiophile 192 sound card, that I have working using the oss drivers, but would like to get it running using the alsa drivers.

I followed the instructions down to the last detail on [http://alsa-project.org/main/index.php/Matrix:Module-ice1724](http://alsa-project.org/main/index.php/Matrix:Module-ice1724) for installing from source alsa, alsa-lib, and alsa-utils.

When I try the following step:
```
 modprobe snd-ice1724 
```

I get the following garbage:

> :/usr/src/alsa$ sudo modprobe snd-ice1724
FATAL: Error inserting snd (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_i2c (/lib/modules/2.6.27-9-generic/kernel/sound/i2c/snd-i2c.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pt2258 (/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-pt2258.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_ak4114 (/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4114.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.27-9-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.27-9-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.27-9-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.27-9-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
FATAL: Error inserting snd_ice1724 (/lib/modules/2.6.27-9-generic/kernel/sound/pci/ice1712/snd-ice1724.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I check dmesg and next to every snd entry there is an Unknown symbol or unknown parameter flag.

So what I´d like to know is what is the workaround/fix for this.

I´ve installed the latest versions of alsa, alsa-lib and alsa-utils...

Thanks in advance.

---

### Post by lex1015 on 2009-10-27
I'm not sure if it's worth opening a new thread since I'm having the exact same problem with my Ensoniq ES1371. I too have the latest version of ALSA installed, so by now I have alsa-driver, alsa-lib and alsa-utils.[B]
 sudo modprobe snd-ens1371[/B] results in

```
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.28-15-generic/kernel/sound/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.28-15-generic/kernel/sound/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting gameport (/lib/modules/2.6.28-15-generic/kernel/drivers/input/gameport/gameport.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ens1371 (/lib/modules/2.6.28-15-generic/kernel/sound/pci/snd-ens1371.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```**dmesg | grep "snd"** gives me the following
```

[  104.626819] snd_ac97_codec: Unknown symbol snd_ctl_add_slave
[  104.628886] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  104.628889] snd_ac97_codec: Unknown symbol ac97_bus_type
[  104.632446] snd_ac97_codec: Unknown symbol snd_ctl_add_slave
[  104.634453] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[  104.634457] snd_ac97_codec: Unknown symbol ac97_bus_type
[18976.062775] snd_ac97_codec: Unknown symbol snd_ctl_add_slave
[18976.064893] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[18976.064896] snd_ac97_codec: Unknown symbol ac97_bus_type
[20298.570068] snd_ac97_codec: disagrees about version of symbol snd_info_register
[20298.570079] snd_ac97_codec: Unknown symbol snd_info_register
[20298.570312] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[20298.570316] snd_ac97_codec: Unknown symbol snd_ctl_add
[20298.570556] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[20298.570559] snd_ac97_codec: Unknown symbol snd_info_free_entry
[20298.570852] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[20298.570855] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[20298.570991] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[20298.570994] snd_ac97_codec: Unknown symbol snd_ctl_new1
[20298.571144] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[20298.571147] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[20298.571321] snd_ac97_codec: disagrees about version of symbol snd_component_add
[20298.571324] snd_ac97_codec: Unknown symbol snd_component_add
[20298.571461] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[20298.571464] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[20298.571591] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[20298.571594] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[20298.571755] snd_ac97_codec: Unknown symbol __snd_printk
[20298.572119] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[20298.572123] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[20298.575630] snd_ac97_codec: disagrees about version of symbol snd_device_new
[20298.575639] snd_ac97_codec: Unknown symbol snd_device_new
[20298.575813] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[20298.575816] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[20298.576112] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[20298.576116] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[23927.019500] snd_ac97_codec: disagrees about version of symbol snd_info_register
[23927.019511] snd_ac97_codec: Unknown symbol snd_info_register
[23927.019744] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[23927.019747] snd_ac97_codec: Unknown symbol snd_ctl_add
[23927.019987] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[23927.019990] snd_ac97_codec: Unknown symbol snd_info_free_entry
[23927.020329] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[23927.020332] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[23927.020468] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[23927.020471] snd_ac97_codec: Unknown symbol snd_ctl_new1
[23927.020621] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[23927.020624] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[23927.020798] snd_ac97_codec: disagrees about version of symbol snd_component_add
[23927.020801] snd_ac97_codec: Unknown symbol snd_component_add
[23927.020938] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[23927.020941] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[23927.021068] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[23927.021071] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[23927.021231] snd_ac97_codec: Unknown symbol __snd_printk
[23927.021541] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[23927.021545] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[23927.021935] snd_ac97_codec: disagrees about version of symbol snd_device_new
[23927.021938] snd_ac97_codec: Unknown symbol snd_device_new
[23927.022111] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[23927.022114] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[23927.022376] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[23927.022380] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[25017.084766] snd_ac97_codec: disagrees about version of symbol snd_info_register
[25017.084777] snd_ac97_codec: Unknown symbol snd_info_register
[25017.085009] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[25017.085013] snd_ac97_codec: Unknown symbol snd_ctl_add
[25017.085252] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[25017.085255] snd_ac97_codec: Unknown symbol snd_info_free_entry
[25017.085549] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[25017.085552] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[25017.085688] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[25017.085691] snd_ac97_codec: Unknown symbol snd_ctl_new1
[25017.085840] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[25017.085843] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[25017.086017] snd_ac97_codec: disagrees about version of symbol snd_component_add
[25017.086020] snd_ac97_codec: Unknown symbol snd_component_add
[25017.086157] snd_ac97_codec: disagrees about version of symbol snd_ctl_make_virtual_master
[25017.086160] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[25017.086287] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[25017.086290] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[25017.086450] snd_ac97_codec: Unknown symbol __snd_printk
[25017.086760] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[25017.086764] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[25017.087153] snd_ac97_codec: disagrees about version of symbol snd_device_new
[25017.087156] snd_ac97_codec: Unknown symbol snd_device_new
[25017.087329] snd_ac97_codec: disagrees about version of symbol _snd_ctl_add_slave
[25017.087332] snd_ac97_codec: Unknown symbol _snd_ctl_add_slave
[25017.087595] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[25017.087598] snd_ac97_codec: Unknown symbol snd_info_create_card_entry


```Has anyone fixed it?
Thanks.

---

### Post by akicks on 2009-11-08
I am also have issues with ice1724:

Output from modprobe snd-ice1724:
```
FATAL: Error inserting snd (/lib/modules/2.6.31-14-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pt2258 (/lib/modules/2.6.31-14-generic/updates/alsa/i2c/other/snd-pt2258.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.31-14-generic/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.31-14-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.31-14-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4114 (/lib/modules/2.6.31-14-generic/updates/alsa/i2c/other/snd-ak4114.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ak4xxx_adda (/lib/modules/2.6.31-14-generic/updates/alsa/i2c/other/snd-ak4xxx-adda.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ac97_bus (/lib/modules/2.6.31-14-generic/updates/alsa/misc/ac97_bus.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.31-14-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_ice17xx_ak4xxx (/lib/modules/2.6.31-14-generic/updates/alsa/pci/ice1712/snd-ice17xx-ak4xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.31-14-generic/updates/alsa/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.31-14-generic/updates/alsa/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ice1724 (/lib/modules/2.6.31-14-generic/updates/alsa/pci/ice1712/snd-ice1724.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Output from lspci -v
```
02:0f.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Flags: medium devsel, IRQ 17
	I/O ports at c800 [size=32]
	I/O ports at cc00 [size=128]
	Capabilities: [80] Power Management version 1
	Kernel modules: snd-ice1724
```

Finally From aplay -l
```
aplay: device_list:223: no soundcards found...
```

I've followed [this]("http://ubuntuforums.org/showthread.php?t=205449") thread to try and get the sound working, but as you can see I've currently had no luck.

---

