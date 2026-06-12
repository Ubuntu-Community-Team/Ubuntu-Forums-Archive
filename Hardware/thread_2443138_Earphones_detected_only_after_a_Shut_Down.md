---
title: "Earphones detected only after a Shut Down"
date: 2020-05-11
forum: Hardware
---

### Post by ngupta9 on 2020-05-11
**Scenario 1**
When the laptop is booted while the earphones are already plugged in.
Result: Earphones work fine.

**Scenario 2**
Earphones are plugged while using Ubuntu.

**Result:** 
[LIST]
[*]No headphone sign is displayed
[*]Sound coming from both the devices; Internal speakers and Earphones
[*]No Auto-mute option in Alsa-mixer
[/LIST]

This is very frustrating. Can someone please suggest how to solve this?

---

### Post by Yellow Pasque on 2020-05-12
> This is very frustrating.
Agreed. I have asked you for more information twice now and you just keep making new threads...

So let's try again. Maybe the thirds time's a charm: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
I think that link/page is fairly self-explanatory. If you don't understand, please ask for clarification instead of making new threads. Thanks.

---

### Post by ngupta9 on 2020-05-21
Apologies for multiple threads. Here is the information:
[http://alsa-project.org/db/?f=40e311718e4125efd3b3b3a3a613178cc01324c2](http://alsa-project.org/db/?f=40e311718e4125efd3b3b3a3a613178cc01324c2)

---

### Post by Yellow Pasque on 2020-05-22
> Lenovo IdeaPad FLEX-14IML
Hmm. I didn't find anything on Google about this model and Linux sound.

This does not seem correct to me (no hp_out pin):
```
snd_hda_codec_conexant hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
```
The only suggestion I have is experimenting with hdajackretask. Unfortunately, I can't be more specific as to which pins to override. It's often a matter of "guess and test".
```
sudo apt-get install alsa-tools-gui
hdajackretask
```

---

