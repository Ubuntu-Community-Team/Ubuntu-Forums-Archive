---
title: "ALC892: no surround sound / only two channels working"
date: 2016-10-13
forum: Hardware
---

### Post by pantalaimon2 on 2016-10-13
Hi,
I have an ALC892 chip on my [B150M]("http://www.asrock.com/mb/Intel/B150M%20Pro4D3/?cat=Specifications") board with a 5.1 sound system connected to it.
While it is possible to select Analog 5.1 output in sound setting (among other options which I've all tried) only the two front speakers will play sound (e.g. when running [COLOR=#000000][FONT=monospace]speaker-test -Dplug:surround51 -c6 -twav)[/FONT][/COLOR] (no LFE, no center, no rear).

I've tried several options as ```
options snd-hda-intel model=3stack-6ch
``` in [FONT=courier new]/etc/modprobe.d/alsa-base.conf[/FONT] with no change at all.

I've also tried adding ```
default-sample-channels = 6
``` to [FONT=courier new]/etc/pulse/daemon.conf
[/FONT]
[FONT=courier new]alsa-info [/FONT]output: [http://www.alsa-project.org/db/?f=8e7b0788cde8967048959d50a57b0bb214ddc7fb](http://www.alsa-project.org/db/?f=8e7b0788cde8967048959d50a57b0bb214ddc7fb)

Watching [[FONT=courier new]HDA-Analyzer[/FONT]]("http://www.alsa-project.org/main/index.php/HDA_Analyzer") while changing the settings from Analog Stereo Output to Analog 5.1 output gives
```

Watching 1 cards
======================================
Diff for codec 0/0 (0x10ec0892):
--- 
+++ 
@@ -14,42 +14,42 @@
 GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
   IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
   IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
 Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
   Device: name="ALC892 Analog", type="Audio", device=0
   Control: name="Front Playback Volume", index=0, device=0
     ControlAmp: chs=3, dir=1, idx=0, ofs=0
   Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
-  Amp-Out vals: [0x36 0x36]
+  Amp-Out vals: [0x40 0x40]
   Converter: stream=1, channel=0
   PCM:
     rates [0x560]: 44100 48000 96000 192000
     bits [0xe]: 16 20 24
     formats [0x1]: PCM
   Power: setting=D0, actual=D0
 Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
   Control: name="Surround Playback Volume", index=0, device=0
     ControlAmp: chs=3, dir=1, idx=0, ofs=0
   Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
-  Amp-Out vals: [0x36 0x36]
-  Converter: stream=1, channel=0
+  Amp-Out vals: [0x40 0x40]
+  Converter: stream=1, channel=2
   PCM:
     rates [0x560]: 44100 48000 96000 192000
     bits [0xe]: 16 20 24
     formats [0x1]: PCM
   Power: setting=D0, actual=D0
 Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
   Control: name="Center Playback Volume", index=0, device=0
     ControlAmp: chs=1, dir=1, idx=0, ofs=0
   Control: name="LFE Playback Volume", index=0, device=0
     ControlAmp: chs=2, dir=1, idx=0, ofs=0
   Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
-  Amp-Out vals: [0x36 0x36]
-  Converter: stream=1, channel=0
+  Amp-Out vals: [0x40 0x40]
+  Converter: stream=1, channel=4
   PCM:
     rates [0x560]: 44100 48000 96000 192000
     bits [0xe]: 16 20 24
     formats [0x1]: PCM
   Power: setting=D0, actual=D0
 Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
   Control: name="Headphone Playback Volume", index=0, device=0
     ControlAmp: chs=3, dir=1, idx=0, ofs=0

```

[codecgraph]("http://helllabs.org/codecgraph/") [URL="http://imgh.us/codec0_1.svg"]output:
[IMG]http://imgh.us/codec0_2.svg[/IMG][/URL]

I'm running Linux 4.8.0-22-generic / Ubuntu 16.10

I'm happy to provide you with more information/help debug this issue.

---

### Post by pantalaimon2 on 2016-10-13
Hooray!

I was successful fiddling around with [FONT=courier new]hdajackretask[/FONT] from the [FONT=courier new]alsa-tools-gui[/FONT] package!

I used mostly trial & error and my config is probably a bit messy, I'll clean it up tomorrow after some sleep ;)

Is there some way to share it so that not everyone using this board has to go though that arduous process? I don't even know where the config file is located that this tool generated.

---

### Post by pantalaimon2 on 2016-10-17
The generated [FONT=courier new]/lib/firmware/hda-jack-retask.fw[/FONT] is

```

[codec]
0x10ec0892 0x18498892 0


[pincfg]
0x11 0x411111f0
0x12 0x411111f0
0x14 0x01014010
0x15 0x40f000f0
0x16 0x40f000f0
0x17 0x411111f0
0x18 0x01014011
0x19 0x02a19950
0x1a 0x01014012
0x1b 0x02214120
0x1c 0x411111f0
0x1d 0x4005e601
0x1e 0x01452130
0x1f 0x411111f0


[model]
auto

```

---

