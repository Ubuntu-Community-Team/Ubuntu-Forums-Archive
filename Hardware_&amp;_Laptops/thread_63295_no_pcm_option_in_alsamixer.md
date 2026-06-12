---
title: "no pcm option in alsamixer"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by scaza on 2005-09-07
Anyone have any ideas why the PCM bar wouldn't have an MM box.  It can't be muted or unmuted.  All I can hear is silence.  I've attached a picure for clarity. ](*,)

---

### Post by skoal on 2005-09-07
Hmm, interesting.  Interesting, indeed! I thought all soundcards allowed you to control the PCM device this way.  Yours, however, may not.  I dunno.

Open up a terminal and type 'amixer'.  Look for the Mixer Control entry 'PCM'.  It should be your second entry, so you'll have to scroll back up to the top.  It will look something like this:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 31 [100%] [on]
  Front Right: Playback 31 [100%] [on]
```
Post back those lines for just that PCM control.

You have Intel/Realtek integrated driver? If so, what motherboard?  Do you have the OSS modules loaded as well?  It shouldn't matter if they are or not, but maybe they affect the controls in some way.  Here's my output (as an example, showing the Alsa OSS compat mods):
```
skoal@morpheus:///etc/init.d $ lsmod |grep "pcm\|oss"
snd_pcm_oss            53536  0 
snd_mixer_oss          19968  1 snd_pcm_oss
snd_pcm                95240  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25860  2 snd_emu10k1,snd_pcm
snd_page_alloc         10244  2 snd_emu10k1,snd_pcm
snd                    56292  15 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
```

\\//_

---

### Post by scaza on 2005-09-09
Okay, I've now fixed the now sound problem. so I'm not to worried anymore.  But out of curiosity this was what amixer returned.  I have a few less capabilites then you, so maybe that's what is doing it. or maybe it just can't be muted.

```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
``` 

im not sure what the motherboard is, but I am pretty sure oss modules are loaded.
```
pcmcia                 22244  2
pcmcia_core            57984  2 pcmcia,yenta_socket
snd_pcm_oss            54016  1
snd_mixer_oss          20320  2 snd_pcm_oss
snd_pcm                94632  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26148  1 snd_pcm
snd                    59460  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc          9988  2 snd_hda_intel,snd_pcm
``` 


And for those who may be interested in what stopped the silence:
After following many different instructions on how to install upgrades of alsa with little success I discovered realtek driver pack
[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True)

---

