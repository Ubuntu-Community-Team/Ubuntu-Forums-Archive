---
title: "Sound not working."
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by Nexact on 2007-03-06
Hello, 

I've recently installed Ubuntu... and ... My sound is not working.

here's my lspci: 
```

nexact@nexod:~$ lspci
....
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
....

```

lsmod | grep snd
```

nexact@nexod:~$ lsmod | grep snd
snd_atiixp_modem       16136  1 
snd_atiixp             19852  0 
snd_ac97_codec         96672  2 snd_atiixp_modem,snd_atiixp
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  3 snd_atiixp_modem,snd_atiixp,snd_pcm

```

alsamixer:
```

alsamixer: function snd_ctl_open failed for default: No such device

```


If anyone could tell me some hints or solution to fix this problem... thanks !

- Nexact

---

### Post by Nexact on 2007-03-06
Bump ! anyone ?

---

### Post by Nexact on 2007-03-07
I've fixed my problem.. i've booted on generic kernel, everything was fine.. so I guess, i'll need to compile my own kernel.

---

