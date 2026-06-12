---
title: "problem with sound on Vostro 1320"
date: 2009-08-02
forum: Hardware
---

### Post by DJDANG on 2009-08-02
Hi there,
I'm having trouble to configure my laptop Dell Vostro 1320. There's a problem with the headphones port, when I plug any headphone the speaker doesn't stop the sound... It's very annoying!
Could anyone help me with this?
How to fix this issue?
Thanks in advance,

Daniel

---

### Post by eligos on 2009-08-02
I have the same laptop and the same problem

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf6500000 irq 22
```

```
$ lsmod | grep -i snd
snd_hda_intel         433844  4 
snd_pcm                83204  2 snd_hda_intel
snd_seq                57008  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  1 snd_seq
snd                    62628  12 snd_hda_intel,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

---

