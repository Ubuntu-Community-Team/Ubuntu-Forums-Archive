---
title: "AMD Turion X2 will not scale past 800mhz"
date: 2011-09-25
forum: Hardware
---

### Post by durrell on 2011-09-25
This seems to be happening in all variants of Ubuntu. I got it to scale past 800mhz in Debian, but for some reason Ubuntu's (and Mint's) kernel seems to lock it to 800mhz. I'm hoping someone here can point me in the right direction for how to get this fixed. I have read up a LOT on it, and discovered that part of the problem was the 65w travel adapter I was using. But I changed over to a normal 90w power adapter and I'm still seeing 800mhz in Ubuntu while the BIOS is reporting 2.3ghz.

This is a Dell Latitude D531, FWIW. 

I can't get it to do anything in cpufreq-utils. Here's the output:

```

cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 109 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.30 GHz:0.00%, 2.20 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 800 MHz:100.00%
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 109 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.20 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.30 GHz:0.00%, 2.20 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 800 MHz:100.00%

```

/proc/cpuinfo
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-66
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips	: 1596.46
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-66
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips	: 1596.67
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```

lsmod
```

Module                  Size  Used by
michael_mic            12612  4 
arc4                   12529  2 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
binfmt_misc            17565  1 
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17606  0 
dell_wmi               12681  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13898  1 dell_wmi
lib80211_crypt_tkip    17387  0 
dell_laptop            13827  0 
wl                   2568244  0 
dcdbas                 14438  1 dell_laptop
pcmcia                 49166  0 
snd_timer              29602  2 snd_pcm,snd_seq
yenta_socket           27846  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
edac_core              53845  0 
pcmcia_rsrc            18372  1 yenta_socket
serio_raw              13166  0 
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                982152  2 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_mce_amd           23464  0 
k8temp                 13016  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13744  0 
ttm                    76664  1 radeon
drm_kms_helper         42136  1 radeon
drm                   227534  4 radeon,ttm,drm_kms_helper
i2c_piix4              13303  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13400  1 radeon
shpchp                 37297  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13165  0 
ahci                   25951  2 
libahci                26642  1 ahci
tg3                   141750  0 

```

---

