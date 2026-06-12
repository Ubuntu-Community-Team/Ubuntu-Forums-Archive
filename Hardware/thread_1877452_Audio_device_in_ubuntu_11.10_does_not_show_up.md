---
title: "Audio device in ubuntu 11.10 does not show up"
date: 2011-11-08
forum: Hardware
---

### Post by kiyu2keith on 2011-11-08
My device seems like it does not show up in the sound settings and since  I'm new in ubuntu I really don't know how to fix it. I tried several  things from forums but to no avail.

aplay -l:
aplay: device_list:240: no soundcards found...

lspci -v:

80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: fast devsel, IRQ 17
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel


this is the output I get when I type those commands.

Can you give me any solution that may work??

Thanks in advance..

---

### Post by MoreOrLess on 2011-11-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
That will tell you more (though you probably won't understand too much of it ;P )

---

### Post by wannabegeek on 2011-11-15
same problem here...

I had audio a few days ago....today it's gone..... no devices show with aplay -l
but an audio device is listed in lspic.....


anybody got any ideas.....so far 11.10 has been really buggy.....I mean lots of stuff don't work...

I'd switch to another more stable release but I need the latest video drivers....

I think I may have to learn how to compile a costume kernel with the 11.10 video in it...

I'll post back when I figure it out....

wng

---

