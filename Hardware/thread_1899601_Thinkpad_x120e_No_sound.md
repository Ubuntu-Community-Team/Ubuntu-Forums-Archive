---
title: "Thinkpad x120e No sound"
date: 2011-12-23
forum: Hardware
---

### Post by tip120 on 2011-12-23
Hi there. I've googled around a bit and searched over the forums but haven't been able to find anything to help my issue. 

I just installed Lubuntu 11.10 x64 on my Thinkpad x120e. Everything seems to work perfectly, with the exception of sound.

I have no sound whatsoever. The Fn + Vol buttons do nothing at all, and I can get no sound out of the internal speakers, headset jack, nor the HDMI audio out.

The weird part is, alsamixer displays the hdmi audio device, and the Intel audio device as well, so it seems like the hardware is being detected, I'm just not getting any sound, with any alsamixer volume settings. 

Anyone have any ideas? I'm not sure what to do about this.

---

### Post by tip120 on 2011-12-24
No one? :(

---

### Post by skomra on 2012-03-02
I had a similar problem with my x120e after I upgraded to 8gb of memory from crucial. I put back in the original 2gb of memory and the sound works again. I'd be curious to find out how much memory you have.

---

### Post by wnelson on 2012-03-03
Give the following a try. Create .asoundrc in your home directory add the following.

```
pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1 
}

pcm.dsp0 {
    type plug
    slave.pcm "dmix"
    # A hint is required for listing the device in some GUIs, e.g. Phonon configuration.
    hint {
         show on
         description "My dmix dsp0"
    }
}
# mixer0 can stay unchanged, because
# it isn't used anyway, I guess ;)
ctl.mixer0 {
    type hw
    card 1
}

```

Walt

---

### Post by geet89 on 2012-05-03
omg!  i had this same problem and now after making the file as walt said, my audio is working perfectly... thank you so much walt

---

