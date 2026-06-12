---
title: "Lubuntu 20.04 LTS, dual audio issue"
date: 2021-02-21
forum: Hardware
---

### Post by mikeymikec on 2021-02-21
My PC has a Realtek (ALC1150) onboard audio chip with analog out connected to my hi-fi, and I have a graphics card with a HDMI output in use.

After a clean-install of Lubuntu 20.04 LTS, it seems that if the hi-fi isn't switched on then Lubuntu defaults to the HDMI audio output but doesn't give me the option to switch back to the Realtek analog out.  When I did the install and rebooted it worked (pretty sure the hi-fi was on), then rebooted later with the hi-fi off (switched to HDMI), then rebooted again with the hi-fi on (realtek default, yay).

It's a PITA to have to remember to switch the hi-fi on before the computer.  In the volume control mixer I've set the HDMI audio out to be the fallback but I doubt that's enough to fix the issue because when the issue occurred, the volume control mixer didn't even acknowledge the existence of the realtek audio device.

---

### Post by TheFu on 2021-02-21
**pavucontrol** will control inputs and output seen by pulseadio.
There are other ways too.

---

### Post by mikeymikec on 2021-02-22
When I mentioned the volume control mixer, turns out that is actually pavucontrol.

---

### Post by TheFu on 2021-02-22
> **mikeymikec said:**
> When I mentioned the volume control mixer, turns out that is actually pavucontrol.

If the devices aren't seen in pavcontrol, that means there aren't any device drivers loaded. You need to manually load them.  To figure out which drivers are missing, I'd boot twice with no other differences.
[LIST]
[*]Without the connection
[*]With the connection
[/LIST]
In both boots, capture a list of loaded kernel modules - use **lsmod** for that.
Compare those files. Audio drivers often have 3-5 modules that get loaded into the kernel. Those are the ones that need to be loaded. You can use **modprobe** or **insmod** to load the modules.  Order matters, so a little trial-error will be needed. In general, look for the module to load first that isn't showing any dependencies in the **lsmod** output.

Using **rmmod** as you figure which order to load the modules will likely be needed too.

Create a little script that loads the modules in the correct order.

This is no guarantee and if the plug isn't connected, expect failure. Sometimes modules depend on finding hardware only during boot and there isn't anything anyone can do about that.

Hope this provides a path to a working solution for you.

---

### Post by mikeymikec on 2021-02-22
In case it becomes relevant, sound is currently working in this session and here's the output of dmesg and lsmod:

```

dmesg | grep snd
[    4.351546] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    4.351852] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[    4.351854] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[    4.364962] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
[    4.367672] snd_hda_codec_realtek hdaudioC0D0: ALC1150: SKU not ready 0x00000000
[    4.368212] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC1150: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    4.368213] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.368213] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    4.368214] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.368215] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[    4.368215] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.368216] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    4.368217] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    4.368218] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a

```

```

lsmod | grep snd
snd_hda_codec_realtek   126976  1
snd_hda_codec_hdmi     61440  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         135168  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    90112  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd

```

---

