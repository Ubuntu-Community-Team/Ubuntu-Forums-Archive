---
title: "My graphics card is (literally) screaming"
date: 2008-09-08
forum: Hardware
---

### Post by masterofthemelee on 2008-09-08
I just installed Ubuntu, installed drivers, and just now went to select a screen saver.

Everything was fine, until I picked a screen saver that rendered in 3D.

My graphics card let out this high pitched extremely loud squeak until I selected another screen saver (a 2D one).  Then I tried a DIFFERENT screen saver which turned out to be 3D and the scream returned.

I played around a little bit and noticed that the screen savers which seem to run at a lower framerate have a lower pitched scream.

What the hell?  Windows never did this.  Is this a hardware problem (I'm pretty sure EVGA's warranty covers banshee cards)?

---

### Post by starcannon on 2008-09-08
My first response based on limited information is overheating in 3d mode.
I have never heard of this before, I've run evga nvidia cards, and never had this happen. 

Lets get some diagnostics:
please post the results of these command line codes:
```
lshw -class display
```

Lets find out if direct rendering is on:
```
glxinfo | grep direct
```

And might as well look at your loaded kernel modules:
```
lsmod
```

Be sure to put a nice bold label between each one in the post, makes looking through them a wee bit easier on the eyes.

---

### Post by masterofthemelee on 2008-09-08
**lshw -class display**

 *-display               
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTX]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia


**glxinfo | grep direct**

direct rendering: Yes
direct rendering: Yes


**lsmod**

Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_stats           7104  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  3 snd_emu10k1_synth
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
emu10k1_gp              4608  0 
gameport               16008  2 emu10k1_gp
evdev                  13056  5 
nvidia               7825536  48 
psmouse                40336  0 
serio_raw               7940  0 
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
agpgart                34760  1 nvidia
snd_hda_intel         344728  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd_hwdep              10500  3 snd_emux_synth,snd_emu10k1,snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
soundcore               8800  1 snd
i2c_nforce2             7680  0 
i2c_core               24832  2 nvidia,i2c_nforce2
pcspkr                  4224  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
usbhid                 31872  0 
hid                    38784  1 usbhid
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
pata_amd               14212  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
forcedeth              51980  0 
ohci_hcd               25348  0 
ehci_hcd               37900  0 
pata_acpi               8320  0 
sata_nv                27528  2 
libata                159344  4 ata_generic,pata_amd,pata_acpi,sata_nv
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
usbcore               146028  4 usbhid,ohci_hcd,ehci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by masterofthemelee on 2008-09-08
**New problem**

I, uh, closed the screen saver selector because of the awful noise, but didn't realize I was selecting one of the 3D ones.

...and now when I try to open the screen saver selector it crashes, meaning if I leave the computer alone for ten minutes its going have a big problem.  I need terminal commands on how to change the screen saver to just a blank screen.  Or pretty much anything that isn't 3D.

---

### Post by starcannon on 2008-09-08
run this: 

```
gconf-editor
```

go to:

apps/gnome-screensaver

then double click on the "themes" key
then click the offending screensaver or screensaves, and click remove

GL and I'd install nvidia-settings and look at the gpu temps when something is making it scream like that.

---

### Post by masterofthemelee on 2008-09-08
bash: gconf-edit: command not found

---

### Post by starcannon on 2008-09-08
ack my bad:

```
gconf-editor
```

that'll do it.

---

### Post by masterofthemelee on 2008-09-08
nvidia-settings says its running at 71 degrees C while idle and 82 degrees C while rendering one of those 3D screen savers.

---

### Post by starcannon on 2008-09-08
I'm running a couple 7950gt's in SLI mode, they run 45C idle, and 50C under a 3d screensaver load. I'll have to peek at them after a session of UT2k4 one of these days. I'd get some wind on that card.

---

