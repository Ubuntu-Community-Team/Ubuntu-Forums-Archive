---
title: "background noise after upgrading to 19.04"
date: 2019-04-19
forum: Hardware
---

### Post by ground21 on 2019-04-19
Just after upgrading 18.10 to 19.04 I noticed there is some background noise from speakers. It's quiet but audible and really annoying. I have ALC1150 integrated on Z170 based motherboard if it matters. 
I also noticed that the **noise is gone for 5 seconds after emitting any sound** (like playing a song/movie for a second or just clicking somewhere on volume bar so that system volume changes and audio feedback sound is played).
Please help me troubleshooting this.

---

### Post by alexprengere on 2019-04-20
I have the exact same issue. After upgrading from 18.10 to 19.04, my speakers make this clicking noise every second or so, but only when no sound is being played. It is really annoying and playing with alsamixer options did not fix it.

---

### Post by 0x656b694d on 2019-04-20
If you have intel hda, sounds like adding (or modifying if exists)
```

options snd-hda-intel power_save=0 power_save_controller=N

```
to /etc/modprobe.d/alsa-base.conf helps.

```

$ modinfo snd-hda-intel | grep power_save
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

---

### Post by alexprengere on 2019-04-20
This fixes it for me. Thanks!

---

### Post by arcman7 on 2019-04-20
I'm having audio feedback from speakers as well from time to time. I'm still using 18.04 LTS  Motherboard is a AsRock AB350 Pro4.  Sometimes it goes and goes and sometimes it goes away.

---

### Post by ground21 on 2019-04-22
> **0x656b694d said:**
> If you have intel hda, sounds like adding (or modifying if exists)
```

options snd-hda-intel power_save=0 power_save_controller=N

```
to /etc/modprobe.d/alsa-base.conf helps.

```

$ modinfo snd-hda-intel | grep power_save
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

I have ALC1150. I have no idea if executing the command gives any reasonable output in my case, but here it is:
```

&#10140;  ~ modinfo snd-hda-intel | grep power_save
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

```

&#10140;  ~ lsmod | grep snd 
snd_hda_codec_hdmi     53248  1
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_intel          40960  3
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    81920  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd

```

Should I still modify /etc/modprobe.d/alsa-base.conf?


Update: I did modify the file and the issue seems to be gone. Thanks @0x656b694d

---

### Post by Odzinic on 2019-07-09
> **0x656b694d said:**
> If you have intel hda, sounds like adding (or modifying if exists)
```

options snd-hda-intel power_save=0 power_save_controller=N

```
to /etc/modprobe.d/alsa-base.conf helps.

```

$ modinfo snd-hda-intel | grep power_save
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (xint)
parm:           power_save_controller:Reset controller in power save mode. (bool)

```

I just attempted this on Kubuntu 19.04. I recall this fix working without a problem in the past but now the powersaving click keeps happening even though it seems powersaving is disabled. Any ideas on what else could be causing this?

---

### Post by linkchain on 2019-08-17
Your solution worked for me, thank you!

---

### Post by satya_461 on 2020-07-14
Thanks a lot! This worked for me! I am starting to hate linux for these reasons.. "too many basic things dont work either on upgrade or with devices".. Having hardtime to use airpods properly. ie. use airpods for mic.

---

### Post by noutram on 2020-08-23
I had this issue with Mint 20 and Ubuntu 20.04. This solution fixed the clicking, but now the machine won't shutdown properly. Any thoughts?

---

### Post by coffeecat on 2020-08-23
Back to sleep, old thread.

@noutram, if you need help, please start your own thread.

---

