---
title: "[SOLVED] Problem with sound after kernel recompile"
date: 2009-01-07
forum: Hardware
---

### Post by microbolt on 2009-01-07
I'm hoping that this is just something simple and that I'm overlooking.  I just upgraded my kernel to 2.6.28 and I'm having problems with my audio.  I've also tried downloading the alsa drivers and compiling them with no luck as well.  The sound still works in my 2.6.24-22 kernel with no problems.  Is there maybe some files left over from it that are conflicting with the new kernel?  Let me know any other info that i can post to help with troubleshooting it.  I've been searching through google for the last few hours and havn't had any luck yet.

lspci output
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01c2
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Unknown (5)

```

lsmod on the 2.6.28 kernel
```

Module                  Size  Used by
soundcore               2692  0 
isofs                  32548  1 
udf                    80292  0 
crc_itu_t               3200  1 udf
af_packet              18048  4 
ipv6                  245364  10 
i915                   56964  2 
drm                    86568  3 i915
rfcomm                 34448  2 
l2cap                  21760  13 rfcomm
bluetooth              57700  4 rfcomm,l2cap
rfkill_input            5888  0 
ppdev                   8452  0 
acpi_cpufreq            8972  1 
cpufreq_stats           6020  0 
cpufreq_userspace       4100  0 
cpufreq_ondemand        8076  1 
cpufreq_powersave       2560  0 
cpufreq_conservative     7176  0 
freq_table              5504  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               4480  0 
sbs                    12168  0 
sbshc                   6272  1 sbs
iptable_filter          3712  0 
ip_tables              12048  1 iptable_filter
x_tables               15620  1 ip_tables
parport_pc             33060  0 
lp                      9988  0 
parport                35180  3 ppdev,parport_pc,lp
arc4                    2944  2 
ecb                     3840  2 
b43                   141088  0 
rfkill                 11852  3 rfkill_input,b43
mac80211              200184  1 b43
joydev                 10688  0 
cfg80211               31760  1 mac80211
pcmcia                 35660  0 
led_class               5124  1 b43
input_polldev           4872  1 b43
snd_page_alloc         10248  0 
psmouse                42128  0 
pcspkr                  3584  0 
serio_raw               6276  0 
yenta_socket           24844  1 
rsrc_nonstatic         12160  1 yenta_socket
pcmcia_core            35988  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               12068  0 
iTCO_vendor_support     4740  1 iTCO_wdt
shpchp                 32660  0 
pci_hotplug            27936  1 shpchp
video                  17808  0 
output                  3968  1 video
button                  7056  0 
battery                11140  0 
ac                      5252  0 
intel_agp              26556  1 
agpgart                34632  3 drm,intel_agp
evdev                  10528  8 
dcdbas                  8224  0 
ext3                  123656  1 
jbd                    46612  1 ext3
mbcache                 8708  1 ext3
sg                     28980  0 
sr_mod                 15044  1 
cdrom                  35488  1 sr_mod
sd_mod                 28824  3 
ata_piix               22532  3 
ata_generic             5892  0 
pata_acpi               5120  0 
libata                168992  3 ata_piix,ata_generic,pata_acpi
scsi_mod              149140  4 sg,sr_mod,sd_mod,libata
ehci_hcd               35084  0 
uhci_hcd               23312  0 
tg3                   122500  0 
libphy                 21632  1 tg3
usbcore               141456  3 ehci_hcd,uhci_hcd
ssb                    34180  1 b43
thermal                16412  0 
processor              41132  4 acpi_cpufreq,thermal
fan                     5380  0 
thermal_sys            11560  4 video,thermal,processor,fan
fuse                   51996  3 

```

lsmod on my working 2.6.24-22
```
Module                  Size  Used by
isofs                  36388  1 
udf                    88612  0 
af_packet              23812  4 
ipv6                  267780  10 
i915                   32512  2 
drm                    82452  3 i915
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
rfkill_input            5760  0 
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  1 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_conservative     8712  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5632  0 
bay                     6912  0 
dock                   11280  1 bay
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_hda_intel         344856  3 
b43                   144548  0 
rfkill                  8596  3 rfkill_input,b43
snd_pcm_oss            42144  0 
mac80211              165652  1 b43
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
cfg80211               15112  1 mac80211
snd_hwdep              10500  1 snd_hda_intel
led_class               6020  1 b43
input_polldev           5896  1 b43
snd_seq_dummy           4868  0 
wl                   1073940  0 
ieee80211_crypt         7040  1 wl
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  19856  0 
output                  4736  1 video
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               7940  0 
ac                      6916  0 
battery                14212  0 
intel_agp              25492  1 
wmi_acer                9644  0 
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
dcdbas                  9504  0 
evdev                  13056  9 
soundcore               8800  1 snd
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_piix               19588  3 
ata_generic             8324  0 
pata_acpi               8320  0 
tg3                   116228  0 
libata                159344  3 ata_piix,ata_generic,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
ssb                    34308  1 b43
uhci_hcd               27024  0 
usbcore               146412  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

```

heres the errors I get when i try to modprobe snd-hda-intel
```
FATAL: Error inserting snd (/lib/modules/2.6.28-core2/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-core2/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-core2/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.28-core2/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-core2/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.28-core2/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-core2/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and the matching dmesg errors:

```
[ 2432.488240] snd: Unknown symbol unregister_sound_special
[ 2432.488474] snd: Unknown symbol register_sound_special_device
[ 2432.490739] snd_hwdep: Unknown symbol snd_info_register
[ 2432.490849] snd_hwdep: Unknown symbol snd_info_create_module_entry
[ 2432.491020] snd_hwdep: Unknown symbol snd_info_free_entry
[ 2432.491128] snd_hwdep: Unknown symbol snd_unregister_oss_device
[ 2432.491224] snd_hwdep: Unknown symbol snd_verbose_printk
[ 2432.491317] snd_hwdep: Unknown symbol snd_register_oss_device
[ 2432.491407] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[ 2432.491494] snd_hwdep: Unknown symbol snd_card_file_add
[ 2432.491607] snd_hwdep: Unknown symbol snd_iprintf
[ 2432.491694] snd_hwdep: Unknown symbol snd_major
[ 2432.491831] snd_hwdep: Unknown symbol snd_unregister_device
[ 2432.491925] snd_hwdep: Unknown symbol snd_device_new
[ 2432.492028] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[ 2432.492138] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[ 2432.492235] snd_hwdep: Unknown symbol snd_lookup_minor_data
[ 2432.492331] snd_hwdep: Unknown symbol snd_card_file_remove
[ 2432.492420] snd_hwdep: Unknown symbol snd_register_device_for_dev
[ 2432.502878] snd_timer: Unknown symbol snd_info_register
[ 2432.502993] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2432.503093] snd_timer: Unknown symbol snd_info_free_entry
[ 2432.503263] snd_timer: Unknown symbol snd_verbose_printk
[ 2432.503377] snd_timer: Unknown symbol snd_iprintf
[ 2432.503507] snd_timer: Unknown symbol snd_ecards_limit
[ 2432.503630] snd_timer: Unknown symbol snd_oss_info_register
[ 2432.503717] snd_timer: Unknown symbol snd_unregister_device
[ 2432.503820] snd_timer: Unknown symbol snd_device_new
[ 2432.504012] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2432.516674] snd: Unknown symbol unregister_sound_special
[ 2432.516908] snd: Unknown symbol register_sound_special_device
[ 2432.519006] snd_timer: Unknown symbol snd_info_register
[ 2432.519117] snd_timer: Unknown symbol snd_info_create_module_entry
[ 2432.519215] snd_timer: Unknown symbol snd_info_free_entry
[ 2432.519382] snd_timer: Unknown symbol snd_verbose_printk
[ 2432.519493] snd_timer: Unknown symbol snd_iprintf
[ 2432.519619] snd_timer: Unknown symbol snd_ecards_limit
[ 2432.519739] snd_timer: Unknown symbol snd_oss_info_register
[ 2432.519825] snd_timer: Unknown symbol snd_unregister_device
[ 2432.519926] snd_timer: Unknown symbol snd_device_new
[ 2432.520159] snd_timer: Unknown symbol snd_register_device_for_dev
[ 2432.521745] snd_pcm: Unknown symbol snd_info_register
[ 2432.521859] snd_pcm: Unknown symbol snd_info_create_module_entry
[ 2432.522018] snd_pcm: Unknown symbol snd_timer_notify
[ 2432.522129] snd_pcm: Unknown symbol snd_timer_interrupt
[ 2432.522217] snd_pcm: Unknown symbol snd_info_free_entry
[ 2432.522304] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[ 2432.522412] snd_pcm: Unknown symbol snd_info_get_str
[ 2432.522642] snd_pcm: Unknown symbol snd_verbose_printk
[ 2432.522836] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[ 2432.522923] snd_pcm: Unknown symbol snd_card_file_add
[ 2432.523056] snd_pcm: Unknown symbol snd_iprintf
[ 2432.523190] snd_pcm: Unknown symbol snd_major
[ 2432.523443] snd_pcm: Unknown symbol snd_unregister_device
[ 2432.523542] snd_pcm: Unknown symbol snd_timer_new
[ 2432.523631] snd_pcm: Unknown symbol snd_device_new
[ 2432.523796] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[ 2432.523983] snd_pcm: Unknown symbol snd_lookup_minor_data
[ 2432.524120] snd_pcm: Unknown symbol snd_info_create_card_entry
[ 2432.524212] snd_pcm: Unknown symbol snd_power_wait
[ 2432.524317] snd_pcm: Unknown symbol snd_device_free
[ 2432.524478] snd_pcm: Unknown symbol snd_card_file_remove
[ 2432.524569] snd_pcm: Unknown symbol snd_register_device_for_dev
[ 2432.524754] snd_pcm: Unknown symbol snd_device_register
[ 2432.524851] snd_pcm: Unknown symbol snd_info_get_line
[ 2432.533687] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[ 2432.533835] snd_hda_intel: Unknown symbol snd_ctl_add
[ 2432.533973] snd_hda_intel: Unknown symbol snd_pcm_new
[ 2432.534085] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 2432.534182] snd_hda_intel: Unknown symbol snd_card_register
[ 2432.534270] snd_hda_intel: Unknown symbol snd_card_free
[ 2432.534380] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 2432.534469] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 2432.534764] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 2432.534852] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[ 2432.534968] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 2432.535171] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 2432.535402] snd_hda_intel: Unknown symbol snd_component_add
[ 2432.535503] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[ 2432.535620] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[ 2432.535736] snd_hda_intel: Unknown symbol snd_card_new
[ 2432.535833] snd_hda_intel: Unknown symbol snd_iprintf
[ 2432.535937] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 2432.536031] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 2432.536151] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 2432.536248] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 2432.536336] snd_hda_intel: Unknown symbol snd_hwdep_new
[ 2432.536468] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 2432.536576] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 2432.536717] snd_hda_intel: Unknown symbol snd_device_new
[ 2432.536808] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[ 2432.536941] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 2432.537090] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 2432.537185] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 2432.537412] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 2432.537683] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 2432.537782] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[ 2432.537942] snd_hda_intel: Unknown symbol snd_pcm_format_width

```

---

### Post by sdennie on 2009-01-07
Did you use the Ubuntu kernel .config as a basis for building your 2.6.28 kernel?  If so, that config doesn't have the snd_hda_intel module turned on in the config.  I'm not sure why your manually built ALSA drivers aren't loading properly but, you can build a new kernel and turn on snd_hda_intel as a module in the kernel config and it should fix your problem.  From "make menuconfig" the option is: Device Drivers->Sound Card Support->Advanced Linux Sound Architecture->Intel HD Audio.

---

### Post by microbolt on 2009-01-07
Yep, sure did use the .config.  I'm recompiling now.  Thanks for your help!

---

### Post by microbolt on 2009-01-08
Worked perfect.  Thanks for the help!

---

