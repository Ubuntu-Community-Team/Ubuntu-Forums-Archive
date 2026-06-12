---
title: "cpu throttling"
date: 2009-05-02
forum: Hardware
---

### Post by pluMmet on 2009-05-02
my dmesg says:

[ 4.723956] PCORE - MSR_FSB_FREQ undefined value<4>p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.

how do I use acpi-cpufreq instead of p4-clockmod?

---

### Post by angelsniper45 on 2009-05-02
Well, why would want to overclock a laptop? If its to much you can fry the clock, thus rendering it useless.

what kind of laptop do you have?

---

### Post by pluMmet on 2009-05-02
It's not a laptop. I thought this was the hardware thread for all computers?

It's a home built dual xeon 5355 system.

I don't want to overclock it...I just saw thes message in my dmesg
and it looked like it needed to be resloved.

Maybe it doesn't matter?

---

### Post by angelsniper45 on 2009-05-02
Ok, i just assumed you had a laptop, my bad.

---

### Post by afrodeity on 2010-11-15
I just upgraded my hardware, moving my sata drives to a a new motherboard with an Intel Duel Core E5400.

I get this mesage in my syslog:

```

p4-clockmod: Warning: EST-capable CPU detected. The acpi-cpufreq module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
```

If i lsmod, there is no p4-clockmod

```

lsmod
Module                  Size  Used by
nfsd                  251019  11 
lockd                  66562  1 nfsd
nfs_acl                 2359  1 nfsd
auth_rpcgss            35611  1 nfsd
sunrpc                199323  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3578  1 nfsd
vboxnetadp              6462  0 
vboxnetflt             15156  0 
vboxdrv               190231  2 vboxnetadp,vboxnetflt
kvm_intel              43586  0 
kvm                   303336  1 kvm_intel
binfmt_misc             6586  1 
snd_hda_codec_realtek   252133  1 
nvidia               9327331  58 
snd_hda_intel          24332  2 
snd_hda_codec          86476  2 snd_hda_codec_realtek,snd_hda_intel
usblp                  10833  0 
snd_hwdep               5181  1 snd_hda_codec
snd_pcm                75575  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4786  0 
snd_rawmidi            17763  1 snd_seq_midi
snd_seq_midi_event      5919  1 snd_seq_midi
snd_seq                47142  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19824  2 snd_pcm,snd_seq
snd_seq_device          5776  3 snd_seq_midi,snd_rawmidi,snd_seq
hwmon_vid               2399  0 
snd                    49949  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
coretemp                5533  0 
led_class               2639  0 
sn9c102               148081  0 
snd_page_alloc          7352  2 snd_hda_intel,snd_pcm
lp                      7400  0 
ppdev                   5245  0 
shpchp                 25357  0 
videodev               68287  1 sn9c102
psmouse                58014  0 
parport_pc             27846  1 
v4l1_compat            13912  1 videodev
parport                32560  3 lp,ppdev,parport_pc
serio_raw               4062  0 
raid10                 22366  0 
raid456                54795  0 
async_raid6_recov       4852  1 raid456
async_pq                3299  2 raid456,async_raid6_recov
raid6_pq               79773  2 async_raid6_recov,async_pq
async_xor               2423  3 raid456,async_raid6_recov,async_pq
xor                    15744  1 async_xor
async_memcpy            1013  2 raid456,async_raid6_recov
async_tx                2207  5 raid456,async_raid6_recov,async_pq,async_xor,async_memcpy
raid1                  20441  0 
raid0                   8687  0 
multipath               6092  0 
linear                  3726  0 
usbhid                 36648  0 
hid                    67454  1 usbhid
uvesafb                23587  1 
r8169                  37363  0 
intel_agp               9913  0 
intel_gtt              13287  1 intel_agp
agpgart                32238  3 nvidia,intel_agp,intel_gtt
mii                     4169  1 r8169

```

wondering if all I need to do is modprobe acpi-cpufreq and add it to /etc/modules?

Do I need to blacklist anything?

---

