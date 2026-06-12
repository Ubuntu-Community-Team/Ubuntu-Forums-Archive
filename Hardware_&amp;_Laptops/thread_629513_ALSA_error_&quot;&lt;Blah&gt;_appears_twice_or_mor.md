---
title: "ALSA error: &quot;&lt;Blah&gt; appears twice or more&quot; on Samsung M60 T7300 Casaby"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by Tycho451 on 2007-12-02
Hi,

I installed Kubuntu 7.10 on a Samsung M60 T7300 Casaby a few days ago and since then I'm trying to get ALSA to work.

I have no sound at all and when I try to start alsamixer I get:
```

ALSA lib simple_none.c:1738:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument 

```

Among the things I tried are:
[LIST]
[*]Build & Install ALSA 1.0.15
[*]Build & Install ALSA from the Mercury (HG) repositories
[*]Build & Install ALSA with help of the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
[*]Ask in #alsa on Freenode.org and do everything they suggested (like:)
[*]Reinstalled ALSA 1.0.15 until tsalsa reported Alsa-driver version: 1.0.15
[*]delete /etc/asound.state
[*]not delete /etc/asound.names because it wasn't there
[*]rename /var/lib/alsa/sound.state
[/LIST]

tsalsa reports:
```

tsalsa version 2007-11-28 So 2. Dez 18:57:58 CET 2007	

Problem: no sound, alsamixer brings error message: "ALSA lib simple_none.c:1738:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more	

       Laptop: Samsung M60 T7300 Casaby	
        plugs: 2 	
        surround sound system: n	
        model options: y	
        number of speakers... 2 	
Distro: Ubuntu 7.10 \n \lDISTRIB_ID=UbuntuDISTRIB_DESCRIPTION="Ubuntu 7.10"	

Release: lsb-release	

System: Linux minerva 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007	
       i686 GNU/Linux	

Vendor/dev id: 	
        8086 284b	

Vendor/dev module: 	
      	

Vendor/device: 8086:284b Subsystem: Samsung Electronics Co Ltd Unknown device c509	

Lspci info: 	
      	00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)	

Alsa driver: 1.0.15	
Alsa lib: 1.0.15	
Alsa utils: 1.0.15	

Alsa modules:	
        snd_hda_intel	

Snd/soundcore: 	
      snd                    56708  9 snd_hda_intel	
      snd_pcm_oss	
      snd_mixer_oss	
      snd_pcm	
      snd_hwdep	
      snd_seq_oss	
      snd_seq	
      snd_timer	
      snd_seq_device	
soundcore               8800  2 snd	

Alsa cards: 	
	 0 [Intel          ]: HDA-Intel - HDA Intel	
	                      HDA Intel at 0xd3500000 irq 22	

Codec: 	

	Codec: Realtek ALC262	

Lsof output: 	


cardcnt: 0 	
Amixer item options for card 0 [Intel] _________________________________	
  : values=off	
'Input Source'  ; Item #0 'Mic'  ; Item #1 'Front Mic'  ; Item #2 'Line'  ; Item #3 'CD'  : values=0	
'Input Source',device=2  ; Item #0 'Mic'  : values=0	
'Input Source',index=1  ; Item #0 'Mic'  ; Item #1 'Front Mic'  ; Item #2 'Line'  ; Item #3 'CD'  : values=0	
'Input Source',index=1,device=2  ; Item #0 'Mic'  : values=0	
'Input Source',index=2  ; Item #0 'Mic'  ; Item #1 'Front Mic'  ; Item #2 'Line'  ; Item #3 'CD'  : values=0	
'Input Source',index=2,device=2  ; Item #0 'Mic'	

Amixer contents for card 0 [Intel] _____________________________________	


Module Parameters:	
snd_hda_intel/parameters/enable:N	
snd_hda_intel/parameters/id:<NULL>	
snd_hda_intel/parameters/index:-1	
snd_hda_intel/parameters/model:<NULL>	
snd_hda_intel/parameters/position_fix:0	
snd_hda_intel/parameters/power_save:0	
snd_hda_intel/parameters/power_save_controller:Y	
snd_hda_intel/parameters/probe_mask:-1	
snd_hda_intel/parameters/single_cmd:N	
snd_pcm_oss/parameters/adsp_map:1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1	
snd_pcm_oss/parameters/dsp_map:0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0	
snd_pcm_oss/parameters/nonblock_open:Y	
snd_pcm/parameters/maximum_substreams:4	
snd_pcm/parameters/preallocate_dma:1	
snd_seq_oss/parameters/maxqlen:1024	
snd_seq_oss/parameters/seq_oss_debug:0	
snd_seq/parameters/seq_client_load:14,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1	
snd_seq/parameters/seq_default_timer_card:-1	
snd_seq/parameters/seq_default_timer_class:1	
snd_seq/parameters/seq_default_timer_device:1	
snd_seq/parameters/seq_default_timer_resolution:0	
snd_seq/parameters/seq_default_timer_sclass:0	
snd_seq/parameters/seq_default_timer_subdevice:0	
snd_timer/parameters/timer_limit:2	


Seq clients: 	
Client info	
  cur  clients : 2	
  peak clients : 2	
  max  clients : 192	

Client   0 : "System" [Kernel]	
  Port   0 : "Timer" (Rwe-)	
  Port   1 : "Announce" (R-e-)	
    Connecting To: 15:0	
Client  15 : "OSS sequencer" [Kernel]	
  Port   0 : "Receiver" (-we-)	
    Connected From: 0:1	

Devices: 	
  0: [ 0]   : control	
  1:        : sequencer	
  4: [ 0- 0]: hardware dependent	
  5: [ 0- 1]: hardware dependent	
  6: [ 0- 2]: hardware dependent	
 16: [ 0- 0]: digital audio playback	
 19: [ 0- 3]: digital audio playback	
 20: [ 0- 4]: digital audio playback	
 22: [ 0- 6]: digital audio playback	
 24: [ 0- 0]: digital audio capture	
 26: [ 0- 2]: digital audio capture	
 27: [ 0- 3]: digital audio capture	
 29: [ 0- 5]: digital audio capture	
 30: [ 0- 6]: digital audio capture	
 33:        : timer	

Lspci -vn: 	
00:00.0 0600: 8086:2a00 (rev 03)	
	Subsystem: 144d:c509	
	Flags: bus master, fast devsel, latency 0	
	Capabilities: <access denied>	

00:01.0 0604: 8086:2a01 (rev 03) (prog-if 00 [Normal decode])	
	Flags: bus master, fast devsel, latency 0	
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0	
	I/O behind bridge: 00002000-00002fff	
	Memory behind bridge: d0000000-d2ffffff	
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff	
	Capabilities: <access denied>	

00:1a.0 0c03: 8086:2834 (rev 03) (prog-if 00 [UHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 16	
	I/O ports at 1800 [size=32]	

00:1a.1 0c03: 8086:2835 (rev 03) (prog-if 00 [UHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 19	
	I/O ports at 1820 [size=32]	

00:1a.7 0c03: 8086:283a (rev 03) (prog-if 20 [EHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 21	
	Memory at d3504000 (32-bit, non-prefetchable) [size=1K]	
	Capabilities: <access denied>	

00:1b.0 0403: 8086:284b (rev 03)	
	Subsystem: 144d:c509	
	Flags: bus master, fast devsel, latency 0, IRQ 22	
	Memory at d3500000 (64-bit, non-prefetchable) [size=16K]	
	Capabilities: <access denied>	

00:1c.0 0604: 8086:283f (rev 03) (prog-if 00 [Normal decode])	
	Flags: bus master, fast devsel, latency 0	
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0	
	Capabilities: <access denied>	

00:1c.1 0604: 8086:2841 (rev 03) (prog-if 00 [Normal decode])	
	Flags: bus master, fast devsel, latency 0	
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0	
	Memory behind bridge: d3100000-d31fffff	
	Capabilities: <access denied>	

00:1c.3 0604: 8086:2845 (rev 03) (prog-if 00 [Normal decode])	
	Flags: bus master, fast devsel, latency 0	
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0	
	I/O behind bridge: 00003000-00003fff	
	Memory behind bridge: d3000000-d30fffff	
	Prefetchable memory behind bridge: 000000008c000000-000000008c0fffff	
	Capabilities: <access denied>	

00:1d.0 0c03: 8086:2830 (rev 03) (prog-if 00 [UHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 20	
	I/O ports at 1840 [size=32]	

00:1d.1 0c03: 8086:2831 (rev 03) (prog-if 00 [UHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 18	
	I/O ports at 1860 [size=32]	

00:1d.2 0c03: 8086:2832 (rev 03) (prog-if 00 [UHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 21	
	I/O ports at 1880 [size=32]	

00:1d.7 0c03: 8086:2836 (rev 03) (prog-if 20 [EHCI])	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0, IRQ 20	
	Memory at d3504400 (32-bit, non-prefetchable) [size=1K]	
	Capabilities: <access denied>	

00:1e.0 0604: 8086:2448 (rev f3) (prog-if 01 [Subtractive decode])	
	Flags: bus master, fast devsel, latency 0	
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32	
	I/O behind bridge: 00004000-00004fff	
	Memory behind bridge: d3200000-d32fffff	
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff	
	Capabilities: <access denied>	

00:1f.0 0601: 8086:2815 (rev 03)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 0	
	Capabilities: <access denied>	

00:1f.2 0101: 8086:2828 (rev 03) (prog-if 80 [Master])	
	Subsystem: 144d:c509	
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18	
	I/O ports at 01f0 [size=8]	
	I/O ports at 03f4 [size=1]	
	I/O ports at 0170 [size=8]	
	I/O ports at 0374 [size=1]	
	I/O ports at 18e0 [size=16]	
	I/O ports at 18d0 [size=16]	
	Capabilities: <access denied>	

00:1f.3 0c05: 8086:283e (rev 03)	
	Subsystem: 144d:c509	
	Flags: medium devsel, IRQ 5	
	Memory at 8c100000 (32-bit, non-prefetchable) [size=256]	
	I/O ports at 1c00 [size=32]	

01:00.0 0300: 10de:0425 (rev a1) (prog-if 00 [VGA])	
	Subsystem: 144d:c509	
	Flags: bus master, fast devsel, latency 0, IRQ 16	
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]	
	Memory at c0000000 (64-bit, prefetchable) [size=256M]	
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]	
	I/O ports at 2000 [size=128]	
	Capabilities: <access denied>	

04:00.0 0280: 8086:4229 (rev 61)	
	Subsystem: 8086:1101	
	Flags: bus master, fast devsel, latency 0, IRQ 17	
	Memory at d3100000 (64-bit, non-prefetchable) [size=8K]	
	Capabilities: <access denied>	

05:00.0 0200: 11ab:4363 (rev 13)	
	Subsystem: 144d:c509	
	Flags: bus master, fast devsel, latency 0, IRQ 18	
	Memory at d3000000 (64-bit, non-prefetchable) [size=16K]	
	I/O ports at 3000 [size=256]	
	[virtual] Expansion ROM at 8c000000 [disabled] [size=128K]	
	Capabilities: <access denied>	

06:09.0 0607: 1180:0476 (rev ba)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 168, IRQ 16	
	Memory at d3200000 (32-bit, non-prefetchable) [size=4K]	
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176	
	Memory window 0: 88000000-8bfff000 (prefetchable)	
	Memory window 1: 90000000-93fff000	
	I/O window 0: 00004000-000040ff	
	I/O window 1: 00004400-000044ff	
	16-bit legacy interface ports at 0001	

06:09.1 0805: 1180:0822 (rev 21)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 32, IRQ 21	
	Memory at d3201000 (32-bit, non-prefetchable) [size=256]	
	Capabilities: <access denied>	

06:09.2 0880: 1180:0843 (rev 11)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 32, IRQ 255	
	Memory at d3201400 (32-bit, non-prefetchable) [size=256]	
	Capabilities: <access denied>	

06:09.3 0880: 1180:0592 (rev 11)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 32, IRQ 255	
	Memory at d3201800 (32-bit, non-prefetchable) [size=256]	
	Capabilities: <access denied>	

06:09.4 0880: 1180:0852 (rev 11)	
	Subsystem: 144d:c509	
	Flags: bus master, medium devsel, latency 32, IRQ 255	
	Memory at d3201c00 (32-bit, non-prefetchable) [size=256]	
	Capabilities: <access denied>	

Codec info: 	
Codec: Realtek ALC262	
Address: 0	
Vendor Id: 0x10ec0262	
Subsystem Id: 0x144dc512	
Revision Id: 0x100002	
No Modem Function Group found	
Default PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Default Amp-In caps: N/A	
Default Amp-Out caps: N/A	
Node 0x02 [Audio Output] wcaps 0x11: Stereo	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Node 0x03 [Audio Output] wcaps 0x11: Stereo	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0x1e]: 16 20 24 32	
    formats [0x1]: PCM	
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x1f 0x1f]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x24	
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x23	
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x22	
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0x1e]: 16 20 24 32	
    formats [0x1]: PCM	
  Connection: 1	
     0x1f	
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In	
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x1f 0x1f] [0x00 0x00] [0x1f 0x1f] [0x80 0x80] [0x1f 0x1f] [0x80 0x80]	
  Connection: 6	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d	
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x1f 0x1f]	
  Connection: 2	
     0x02 0x0b	
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x1f 0x1f]	
  Connection: 2	
     0x03 0x0b	
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00] [0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x00]	
  Connection: 2	
     0x02 0x0b	
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x00 0x00]	
  Pincap 0x083e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x40: OUT	
  Connection: 2	
     0x0c* 0x0d	
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x00 0x00]	
  Pincap 0x083e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0xc0: OUT HP	
  Connection: 2	
     0x0c 0x0d*	
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80]	
  Pincap 0x0810: OUT	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x40: OUT	
  Connection: 1	
     0x0e	
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x24: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo	
  Pincap 0x0820: IN	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x00:	
Node 0x1d [Pin Complex] wcaps 0x400000: Mono	
  Pincap 0x0820: IN	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x00:	
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital	
  Pincap 0x0810: OUT	
  Pin Default 0x18561110: [Jack] Digital Out at Int HDMI	
    Conn = Digital, Color = Black	
  Pin-ctls: 0x00:	
  Connection: 1	
     0x06	
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital	
  Pincap 0x0820: IN	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x00:	
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono	
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono	
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
Codec: Generic 11c1 Si3054	
Address: 1	
Vendor Id: 0x11c11040	
Subsystem Id: 0x2118144d	
Revision Id: 0x100200	
Modem Function Group: 0x1	
Codec: Realtek ALC262	
Address: 2	
Vendor Id: 0x10ec0262	
Subsystem Id: 0x144dc509	
Revision Id: 0x100002	
No Modem Function Group found	
Default PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Default Amp-In caps: N/A	
Default Amp-Out caps: N/A	
Node 0x02 [Audio Output] wcaps 0x11: Stereo	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Node 0x03 [Audio Output] wcaps 0x11: Stereo	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0xe]: 16 20 24	
    formats [0x1]: PCM	
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0x1e]: 16 20 24 32	
    formats [0x1]: PCM	
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x24	
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x23	
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In	
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00]	
  PCM:	
    rates [0x160]: 44100 48000 96000	
    bits [0x6]: 16 20	
    formats [0x1]: PCM	
  Connection: 1	
     0x22	
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital	
  PCM:	
    rates [0x560]: 44100 48000 96000 192000	
    bits [0x1e]: 16 20 24 32	
    formats [0x1]: PCM	
  Connection: 1	
     0x1f	
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In	
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Connection: 6	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d	
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 2	
     0x02 0x0b	
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 2	
     0x03 0x0b	
Node 0x0e [Audio Mixer] wcaps 0x20010e: Mono Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00] [0x00]	
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0	
  Amp-Out vals:  [0x00]	
  Connection: 2	
     0x02 0x0b	
Node 0x0f [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x00 0x00]	
  Pincap 0x083e: IN OUT HP Detect	
  Pin Default 0x99138110: [Fixed] Speaker at Int ATAPI	
    Conn = ATAPI, Color = Purple	
  Pin-ctls: 0x40: OUT	
  Connection: 2	
     0x0c* 0x0d	
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x00 0x00]	
  Pincap 0x083e: IN OUT HP Detect	
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear	
    Conn = 1/8, Color = Green	
  Pin-ctls: 0xc0: OUT HP	
  Connection: 2	
     0x0c* 0x0d	
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80]	
  Pincap 0x0810: OUT	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x40: OUT	
  Connection: 1	
     0x0e	
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono	
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x01a19830: [Jack] Mic at Ext Rear	
    Conn = 1/8, Color = Pink	
  Pin-ctls: 0x24: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0	
  Amp-In vals:  [0x00 0x00] [0x00 0x00]	
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-Out vals:  [0x80 0x80]	
  Pincap 0x08173e: IN OUT HP Detect	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x20: IN	
  Connection: 2	
     0x0c* 0x0d	
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo	
  Pincap 0x0820: IN	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x00:	
Node 0x1d [Pin Complex] wcaps 0x400000: Mono	
  Pincap 0x0820: IN	
  Pin Default 0x4014820d: [N/A] Speaker at Ext N/A	
    Conn = RCA, Color = Purple	
  Pin-ctls: 0x00:	
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital	
  Pincap 0x0810: OUT	
  Pin Default 0x01454120: [Jack] SPDIF Out at Ext Rear	
    Conn = Optical, Color = Green	
  Pin-ctls: 0x00:	
  Connection: 1	
     0x06	
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital	
  Pincap 0x0820: IN	
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear	
    Conn = 1/8, Color = Black	
  Pin-ctls: 0x00:	
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono	
Node 0x21 [Volume Knob Widget] wcaps 0x600080: Mono	
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
Node 0x24 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out	
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1	
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]	
  Amp-Out caps: N/A	
  Amp-Out vals:  [0x00 0x00]	
  Connection: 9	
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x0b	
md5sum tsalsa: 45cd08ed4434de8015a0bed27ff3d469  tsalsa	
1196255218 1196610477 1196618280 1196618280 1196618280 1196618278	
curl: 	
wget: 	/usr/bin/wget	
dialog: 	
tsalsa version 2007-11-28 end:  So 2. Dez 18:58:00 CET 2007 69	
md5sum tsalsa.txt: d686d969987b5b5e693bb792e080ae25  /tmp/tsalsa.txt

```

I'm grateful for any further ideas on how to get sound to work on this Laptop.

---

### Post by Tycho451 on 2007-12-02
*bump*

---

### Post by Yellow Pasque on 2007-12-03
Hi. I can't help you with ALSA problems, but I can give you an alternative to try before you switch OS's. See the link in my sig for details.

---

### Post by Tycho451 on 2007-12-03
Thank you!

Sound does now work! Except for flash.
I did compile [http://www.kaourantin.net/flashplayer/flashsupport.c]("http://www.kaourantin.net/flashplayer/flashsupport.c") after commenting "#define OPENSSL" out with the following commands, but it still doesn't work.

```

cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so
ldd libflashsupport.so
sudo cp libflashsupport.so /usr/lib

```

---

### Post by Yellow Pasque on 2007-12-03
I'm not sure why you downloaded another (possibly older) version of flashsupport.c
You should find this file in /usr/lib/oss/lib
Try removing the file you made and compiling the flashsupport.c included with the .deb, because they've made some updates on it in this latest build.
Also, I've found that it's necessary to create symbolic links to libflashsupport.so in /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins

I should add those steps into my little howto. Thanks.

---

### Post by Tycho451 on 2007-12-03
Sorry, but your HowTo was very vague as to how to compile flashsupport.c so I had to google for another HowTo.
That one suggested to download that file.

Now I did (with help of another HowTo) compile /usr/lib/oss/lib/flashsupport.c

```

sudo apt-get install libssl-dev libssl0.9.8 
cd /usr/lib/oss/lib 
sudo cc -shared -O2 -Wall -Werror -lssl flashsupport.c -o libflashsupport.so 
sudo cp libflashplayer.so /usr/lib

```

And created some links:
```

sudo link /usr/lib/libflashsupport.so /usr/lib/flashplugin-nonfree/libflashsupport.so
sudo link /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins/libflashsupport.so
sudo link /usr/lib/libflashsupport.so /usr/lib/firefox/plugins/libflashsupport.so

```

Then rebooted.

But still no sound (e.g. on youtube.com).
What did I do wrong?

It would be really great if you could write down what exactly to write in the console for people with less experience like me.

Thanks again for your time.

---

### Post by Yellow Pasque on 2007-12-03
Sorry about the vagueness. I'm actually editing the post to include terminal commands as I write. Thunderbird gave me a Thread updated e-mail, and I looked here.

You had the right idea, but the last command in the first block of code should be libflashsupport.so, not libflashplayer.so
You don't need to recompile, just:
```
sudo cp /usr/lib/oss/lib/flashsupport.so /usr/lib
```
Then, do the links like you did in your post above. You shouldn't need to reboot. Just quit FF and restart it. Good luck.

---

### Post by Tycho451 on 2007-12-03
Sorry, I copy & pasted it wrong, but actually typed it right.

Anyway, I checked if define Openssl was commented out then deleted all libflashsupport.so and did everything once more.

Still no sound :(

Here are the commands I used.
Please correct me if I did something wrong:
```

cd /usr/lib/oss/lib
sudo rm ./libflashsupport.so
sudo rm /usr/lib/libflashsupport.so
sudo rm /usr/lib/flashplugin-nonfree/libflashsupport.so
sudo rm /usr/lib/mozilla/plugins/libflashsupport.so
sudo rm /usr/lib/firefox/plugins/libflashsupport.so
sudo cc -shared -O2 -Wall -Werror flashsupport.c -o libflashsupport.so
sudo cp ./libflashsupport.so /usr/lib/libflashsupport.so
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/flashplugin-nonfree/libflashsupport.so
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins/libflashsupport.so
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins/libflashsupport.so

```

/edit: Corrected the link commands as described in your new HowTo.

---

### Post by Yellow Pasque on 2007-12-03
I used symbolic links:
```
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
```

If a bit of disk space isn't of concern to you, you could just straight copy the file to those dirs as well.
Afterthought: I wonder if the permissions need changed on it as well :?
Make sure you chmod 755 /usr/lib/libflashupport.so just to be on the safe side.

---

### Post by Tycho451 on 2007-12-03
I now have symbolic links, too.
Still no diffrence though.

What permissions do your files have? Since I did everything with sudo mine are root/root.

I test with firefox & opera and installed flashplugin-nonfree via adept.

Any ideas what went wrong?

---

### Post by Yellow Pasque on 2007-12-03
I'm not sure. I, for one, downloaded the Flash plugin from Adobe and used nspluginwrapper on it myself.
I also edited my last post:
> Make sure you chmod 755 /usr/lib/libflashupport.so just to be on the safe side.

---

### Post by Tycho451 on 2007-12-03
Did the chmod thing, but no success.
I purged flashplugin-nonfree and installed the .tar.gz version from adobe.com but still no sound.

Should I install nspluginwrapper too?
I can't find it in adept although some site mentioned it should be in multiverse (which I have enabled).

---

### Post by Tycho451 on 2007-12-05
Thanks to the help from the People in the 4Front Forum I got a errormessage from flashsupport.c:
```

ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card

```

Which is weired because it should use OSS.

---

### Post by Tycho451 on 2007-12-05
Ok...all is resolved but a short delay in sound in Flashplayer.

---

