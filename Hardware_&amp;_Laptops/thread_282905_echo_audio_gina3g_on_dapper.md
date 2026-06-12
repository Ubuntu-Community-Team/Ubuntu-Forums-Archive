---
title: "echo audio gina3g on dapper?"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by r2mm on 2006-10-23
Hi everybody, I've been investigating about enabling the alsa driver for my echo audio gina3g card, it seems like it would be possible compiling the required modules or something like that, but  I haven't found any totally clear information about it. Does anybody have some pointers (or even better, a howto)?. I'd really like to use ubuntu for my audio work as I'm very confortable with it and it seems like a not to difficult goal. Any help would be very appreciated, thanks

Arturo

---

### Post by Dark Matter on 2006-10-23
I've gotten my Gina3G to work (sort of).  The problem I'm having is that the headphone output is messed up.  I only have sound coming out of the right ear, but nothing from the left.  I'm not sure how the speaker output is because I haven't been able to test it yet.  I can tell you how to do it, but I need to gather all the commands into a nice, concise guide.

But to everyone else...has anyone actually used this card before?  I ask because I'm perplexed as to how to make the headphone output work correctly.

---

### Post by r2mm on 2006-10-24
Well, that's much better than nothig, wich is what I have so far, so please help me getting there. Maybe my experience could be of help with your problem...

---

### Post by blitze on 2006-10-29
Bump on this but with Edgy?

I can't believe sound is such a Pain in the *** in Linux.  I have a listing of my modules below and it seems that my sound modules are loading in the wrong place.

This is bloody infuriating and the only thing holding me off using Linux as a day to day experience.

Here is my lsmod output

[COLOR="DarkRed"]ipv6                  334432  10 
binfmt_misc            16012  1 
powernow_k8            16576  1 
cpufreq_powersave       3456  0 
cpufreq_stats           9312  0 
cpufreq_userspace       6560  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
tc1100_wmi             10632  0 
video                  22920  0 
battery                14088  0 
container               6656  0 
sbs                    20928  0 
button                  9888  0 
pcc_acpi               19968  0 
sony_acpi               7704  0 
i2c_ec                  7808  1 sbs
ac                      8328  0 
dev_acpi               17540  0 
asus_acpi              21924  0 
hotkey                 14536  0 
dm_mod                 77776  7 
md_mod                 96156  0 
af_packet              29452  2 
fuse                   55056  2 
parport_pc             43560  0 
lp                     16584  0 
parport                49932  2 parport_pc,lp
snd_echo3g             45316  0 
snd_rawmidi            34432  1 snd_echo3g
snd_seq_device         12180  1 snd_rawmidi
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  2 snd_echo3g,snd_pcm_oss
nvidia               5444340  12 
snd_timer              31112  1 snd_pcm
tsdev                  11136  0 
snd                    79016  7 snd_echo3g,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
psmouse                51088  0 
serio_raw              10244  0 
soundcore              14112  1 snd
sg                     44584  0 
usbhid                 51360  0 
snd_page_alloc         13200  2 snd_echo3g,snd_pcm
evdev                  14592  1 
i2c_ali1535             9604  0 
pcspkr                  5248  0 
i2c_ali15x3            10500  0 
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
i2c_ali1563             9988  0 
i2c_core               29312  5 i2c_ec,nvidia,i2c_ali1535,i2c_ali15x3,i2c_ali1563
uli526x                22036  0 
reiserfs              283648  2 
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  4 usbhid,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ahci                   24452  7 
sd_mod                 25728  6 
sata_uli               10500  3 
libata                 88984  2 ahci,sata_uli
scsi_mod              181424  4 sg,ahci,sd_mod,libata
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
alim15x3               15128  0 [permanent]
generic                 7428  0 
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
Module                  Size  Used by[/COLOR]

There is something wrong with the soundcard firmware being recognised i the kernel loading but I tried to lodge a bug report in Edgy Beta and the email bounced back at me.

I hope this gets sorted or I will have to stick with bloody Windows.  ](*,)

---

### Post by wbrown on 2006-11-16
Greetings: 

Try Curtis' wiki page: [https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia) .  I'ts for the mia card but should work for other echo cards.  The key for me on edgy was to just install the latest alsa firmware and copy the installed files to the correct spot.

---

