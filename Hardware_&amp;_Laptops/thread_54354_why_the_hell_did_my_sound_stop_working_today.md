---
title: "why the hell did my sound stop working today?"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by stanwebber on 2005-08-04
i've been running hoary 5.04 for months now & the sound has always worked effortlessly.  now all of a sudden when i boot the machine today it starts beeping wildly when starting alsa then fails.  here is what i get from lspci & lsmod
```
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 01)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 01)
0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 01)
**0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 01)**
0000:02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PD/PRO TMDS
0000:02:02.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:03.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```
```
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
ipt_TCPMSS              4352  1
ipt_limit               2688  8
ip_nat_irc              4464  0
ip_nat_ftp              5104  0
iptable_mangle          2944  0
ipt_LOG                 6656  8
ipt_MASQUERADE          3584  1
iptable_nat            24648  4 ip_nat_irc,ip_nat_ftp,ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  1
ip_conntrack_irc       71856  1 ip_nat_irc
ip_conntrack_ftp       72624  1 ip_nat_ftp
ipt_state               2048  8
ip_conntrack           43668  7 ip_nat_irc,ip_nat_ftp,ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  10 ipt_TCPMSS,ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  33
hostap_crypt_wep        6016  1
af_packet              20744  4
hostap_pci             51728  2
hostap                107784  2 hostap_crypt_wep,hostap_pci
tulip                  46112  0
snd                    50276  0
soundcore               9824  1 snd
snd_page_alloc          9604  0
tsdev                   7488  0
zr364xx                41772  0
videodev                9728  1 zr364xx
i2c_i801                8076  0
i2c_core               21264  1 i2c_i801
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  4 zr364xx,usbhid,uhci_hcd
hw_random               5524  0
pci_hotplug            30512  0
intel_agp              20636  1
agpgart                31784  1 intel_agp
analog                 10784  0
gameport                4608  1 analog
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  0
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  5
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  793
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
```

here is what i was able to dig out of the syslog

```
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_notify
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_interrupt
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_new
Aug  4 07:37:33 localhost kernel: snd_ac97_codec: Unknown symbol snd_interval_refine
Aug  4 07:37:33 localhost kernel: snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_notify
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_interrupt
Aug  4 07:37:33 localhost kernel: snd_pcm: Unknown symbol snd_timer_new
Aug  4 07:37:33 localhost kernel: snd_ac97_codec: Unknown symbol snd_interval_refine
Aug  4 07:37:33 localhost kernel: snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_pcm_close
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_resume
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_new
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_pcm_open
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_set_rate
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_update_bits
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_mixer
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_bus
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_suspend
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_set_ops
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_get_short_name
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_suspend_all
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
Aug  4 07:37:33 localhost kernel: snd_intel8x0: Unknown symbol snd_ac97_tune_hardware
```

*modprobe snd_intel8x0* produces simular errors to the above.  the only recent change to the system was a seemingly unrelated update of the xserver-xorg package.  what the hell happened & where can i look for more info to figure this out?

update:  by the by it's not a hardware failure:  the sound still functions flawlessly in xp

update:  sound works fine booting the system from the live hoary cd.  what in the hell is preventing the modules from loading, manually or otherwise?

---

### Post by evilghost on 2005-08-04
"Usually unknown symbols means some kind of mismatch between the running 
kernel and what it thinks should be its modules. Maybe some kernel 
configuration parameters were changed, and the kernel was recompiled, 
but the modules were not. Or vice versa."

You do anything with the Kernel?

---

### Post by stanwebber on 2005-08-05
[QUOTE=evilghost]You do anything with the Kernel?[/QUOTE]
nope, i would have mentioned it if i had.  sound stopped working clear out of the blue for no discernable reason

update:  i've been struggling with this for an entire day solid now & after pouring over every newsgroup & support site i could find i have to ask why does this shit happen to me & only me & not one single other person on the planet?  i've run across a few people reporting problems that on the surface resemble mine, but turn out to be caused by completely unrelated sources when the solution is had.  going by the axiom help comes to those who help themselves i decided to blindly try anything & everything since fat chance someone out there is gonna help me

well i stumbled onto something while i was randomly loading modules.  if i *modprobe snd_timer* first then that permits me to *modprobe snd_intel8x0* & the rest of the required snd modules all load without errors.  restart alsa & i'm back in business.  now my question is how do i fix my system so all of this is taken care of automatically at boot without my having to manually load the modules?

the alsa-base config files in /etc/modprobe.d & /etc/modutils remain untouched since the day ubuntu was installed & sound did work for months before

---

### Post by stanwebber on 2005-08-06
*depmod -a* fixed everything.  would be nice to know how all this got messed up in the first place

---

