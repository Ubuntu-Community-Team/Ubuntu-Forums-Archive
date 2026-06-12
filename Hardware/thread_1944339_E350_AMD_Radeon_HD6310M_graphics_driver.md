---
title: "E350 AMD Radeon HD6310M graphics driver"
date: 2012-03-21
forum: Hardware
---

### Post by iamnewtolinux on 2012-03-21
I installed Ubuntu10.04 in my LENOVO B575. But it can't support the Radeon HD6310. I got unknown
monitor. And I upgraded ubuntu to 10.10. still got unknown monitor."lspci|grep VGA" output:
VGA compatible controller:ATI TEchnologies device 9802. 
Any clue? Thanks.

---

### Post by wnelson on 2012-03-21
Install 11.10 or greater and it will work with either radeon or fglrx drivers. 

To get sound to work copy the following into your home directory .asoundrc
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

Everything works just fine.

Walt

---

### Post by iamnewtolinux on 2012-03-24
thanks.  I installed the AMD Catalyst Proprietary Driver 8.95. It works fine now.

---

