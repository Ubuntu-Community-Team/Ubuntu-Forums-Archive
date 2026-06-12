---
title: "Sound workarounds no longer work on Inspiron 3500 and Intrepid"
date: 2009-02-18
forum: Hardware
---

### Post by kozimodo on 2009-02-18
Sound never worked out of the box for my old Inspiron 3500 but there were a couple of workarounds.  Neither of them work any longer. Any thoughts on why?  Should I revert to an older version of alsa?
```
blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-card-cs4231
options snd-cs4231 port=0x534 irq=5 dma1=0 dma2=1
```
and
```
blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8
```

---

### Post by kozimodo on 2009-02-20
bump

---

### Post by Michael Longval on 2009-02-21
@Kozimodo

I feel your pain.  I upgraded my (still working) Inspiron 3500 to Xubuntu 8.10. (I use it in my garage/art studio... not afraid to get paint/pastel/fixative on it....)

Sound unfortunately no longer works.  I remember fixing this in a previous post on a 6.06LTS install. 

I'm getting older and don't have as much patience for these fixer uppers.... anyway when I get back from my vacations in 2 weeks I'll have another go at it.  

Good luck until then.

Michael;)

---

