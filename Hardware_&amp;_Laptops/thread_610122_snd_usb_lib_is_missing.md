---
title: "snd_usb_lib is missing"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by HamsterHam on 2007-11-11
rite  i have done ```
lsmod | grep snd
```

and get this

```
snd_hda_intel         288156  4 
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_oss            35456  0 
snd_seq_midi_event      8704  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24580  3 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
snd                    57092  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  
```

rite im missing the usb things frm my soundcard can sum1 help plz.

---

