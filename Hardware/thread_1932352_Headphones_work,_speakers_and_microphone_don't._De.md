---
title: "Headphones work, speakers and microphone don't. Dell M6600, Lucid LTS"
date: 2012-02-27
forum: Hardware
---

### Post by The Dragon Master on 2012-02-27
I have a new Dell M6600 with Lucid LTS installed. I can listen to
sound with headphones but cannot use the built in speakers and microphone.

alsamixer reports that I have 2 sound cards

Device 0
Card: HDA Intel PCH
Chip: IDT ID 76e7
Item: Master [dB gain: 0.00, 0.00]

Device 1 
Card: HD-Audio Generic 
Chip: ATI R6xx HDMI 
Item: S/PDIF 

For device 0, everything is turned to max. This is the default device.
For device 1, there are no user settable controls

Shouting at the gnome-sound-recorder just creates .wav files of white noise.

I've checked everything is unmuted and turned to max in pavucontrol
but pavumeter gives no indication of my voice being detected.

I've tried this hack [http://www.youtube.com/watch?v=YbnBsGPE2UY&feature=related](http://www.youtube.com/watch?v=YbnBsGPE2UY&feature=related)
And I've tried this hack [http://www.youtube.com/watch?v=tULmqpe5Yos](http://www.youtube.com/watch?v=tULmqpe5Yos)

For each hack I then do "sudo alsa force-reload" instead of rebooting,
but neither hack has the desired effect.

If I run aplay without headphone I get

<QUOTE>
aplay -Ddefault:0 -vv ~/somePodcast.mp3
Playing raw data '/somePodcast.mp3' : Unsigned 8 bit, Rate 8000 Hz, Mono
Plug PCM: Rate conversion PCM (48000, sformat=U8)
Converter: libspeex (builtin)
Protocol version: 10002
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 8000
  exact rate   : 8000 (8000/1)
  msbits       : 8
  buffer_size  : 2730
  period_size  : 170
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 170
  period_event : 0
  start_threshold  : 2730
  stop_threshold   : 2730
  silence_threshold: 0
  silence_size : 0
  boundary     : 768426686420090880
Slave: Route conversion PCM (sformat=S32_LE)
  Transformation table:
    0 <- 0
    1 <- 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : U8
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 8
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Soft volume PCM
Control: PCM Playback Volume
min_dB: -51
max_dB: 0
resolution: 256
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Hardware PCM card 0 'HDA Intel PCH' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 32
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tstamp_mode  : ENABLE
  period_step  : 1
  avail_min    : 1024
  period_event : 0
  start_threshold  : 1
  stop_threshold   : 4611686018427387904
  silence_threshold: 0
  silence_size : 4611686018427387904
  boundary     : 4611686018427387904
  appl_ptr     : 0
  hw_ptr       : 0
##################################################+| MAX^C
<UNQUOTE>

How should I proceed from here?
best wishes
TDM

---

### Post by gordintoronto on 2012-02-27
Use the latest version of Ubuntu. Sound has improved with each release.

---

### Post by The Dragon Master on 2012-02-27
> **gordintoronto said:**
> Use the latest version of Ubuntu. Sound has improved with each release.

Thanks gordintoronto for your reply

The reason I use Lucid LTS is because I am using biolinux ([http://nebc.nerc.ac.uk/tools/bio-linux/bio-linux-faq#hwsupp](http://nebc.nerc.ac.uk/tools/bio-linux/bio-linux-faq#hwsupp)) and I would rather like to continue to use biolinux. AFAIK Biolinux doesn't let you upgrade your Ubuntu distribution, i.e. if you choose biolinux you are stuck with Lucid LTS until the next biolinux release is available.

Also, 2 months ago, I tried running latest version of Ubuntu from a live CD and the problem persisted. I'll re-try this test but like I say, I'd really like to keep biolinux working.

all the best
TDB

---

### Post by gordintoronto on 2012-02-27
If you run Sound Preferences, and select the "Output" tab, you could try whatever options you see under "Connector."

If the computer is brand new, full support for the sound might appear along with Ubuntu 12.04. Then you can investigate how "backports" work, to use the latest kernel with your old distro.

---

