---
title: "Simple way to disable mic of my laptop"
date: 2018-06-26
forum: Hardware
---

### Post by edward-n. on 2018-06-26
Hello community,

I bought a Lenovo 720s 13ARR with Ryzen APU and ubuntu runs pretty good on it, better then all other distributions that I've tested.
But I don't know this one thing mentioned in the title: How can I disable the mic? I mean just the mic, not the audio ouput.

My first try was to find out what my sound module is:
```
less /proc/asound/modules
```

It was "snd_hda_intel".

So I blocked it in
```
/etc/modprobe.d/blacklist.conf
```

It's blocked now, but the audio output is blocked too...
Is there a way to block only the mic on a lower level? Unfortunately there is no option for this in the BIOS.

---

### Post by #&amp;thj^% on 2018-06-26
About the best you could accomplish here is to open "alsamixer" and just Mute it.
Using alsamixer as sudo user:
```
sudo alsamixer
```
from there select your sound card using **<F6>** and find the Mic option and Mute it with keyboard **"m".**
This is all that "I" know of with out crippling sound all together.

---

