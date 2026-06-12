---
title: "APCI suspend broken on Oneiric"
date: 2012-02-14
forum: Hardware
---

### Post by haynold on 2012-02-14
Here's a problem I've been struggling with for years: I'm running a HP xw8400 with Oneiric 64-bit. Both [FONT="Courier New"]echo "standby" > /sys/power/state[/FONT] and [FONT="Courier New"]echo "mem" > /sys/power/state[/FONT] as well as the corresponding high-level commands just kill the computer with the screen going blank (but not in power saving mode), the keyboard down, and no reaction to the power button unless I hold it long enough for a hard reset. The system is specified to support these APCI states, and I updated to the latest BIOS 2.38.

Here's my lsmod with the GUI running:

[SIZE="1"]```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
osst                   62035  0 
st                     45135  0 
nvidia              11713772  40 
ppdev                  17113  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
wmi                    19256  1 hp_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
xfs                   835673  1 
i5000_edac             17675  0 
parport_pc             36962  1 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  3 i5000_edac
i5k_amb                13310  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
shpchp                 37345  0 
mptctl                 38983  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
raid10                 30714  0 
raid456                62545  0 
async_pq               13187  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12894  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
aic7xxx               136176  0 
scsi_transport_spi     30689  1 aic7xxx
floppy                 70365  0 
ahci                   26002  3 
libahci                26861  1 ahci
mptsas                 63445  0 
mptscsih               44705  1 mptsas
mptbase               103114  3 mptctl,mptsas,mptscsih
scsi_transport_sas     40558  1 mptsas
raid6_pq               88307  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
tg3                   147729  0 
raid1                  30856  1 
raid0                  17272  0 
multipath              13145  0 
linear                 12928  0 
vesafb                 13809  1 

```[/SIZE]

---

### Post by ahallubuntu on 2012-02-14
Did you check the BIOS Setup for ACPI options?  If there's an option for Standby, make sure it's set to S3 not S1.

But like it or not, some hardware just has lousy ACPI support.  I've found more than one computer that will not Standby reliably in Ubuntu.  Then again, I've found computers that don't Standby reliably in WINDOWS, either!  I simply try to avoid such computers and pick well-designed hardware that plays well with Linux.

My Dell laptop works great with standby/resume - extremely reliable.  So it certainly CAN work.

---

### Post by haynold on 2012-02-14
Yep, the BIOS settings all look correct. HP also sold this system with RHEL, so I suppose they did some testing on Linux at some time...

---

