---
title: "sound card detected in laptop Arima A0851,(chipset Intel )but no sound"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by lignito on 2006-04-03
sound card detected in **laptop Arima A0851**,(chipset Intel )but no sound...
Can any one give me any idea how to enabel this to work,please....](*,)I used alsamixer on a console.  master and pcm channels are not muted .what should I do...

0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with AD1981B at 0xc0000800, irq 17


snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

---

### Post by WickedImp on 2006-04-03
erm.. more details, please? try the following:
```
lsmod | grep snd
```
if you get modules named soundcore, snd_*, etc... then drivers are loaded (maybe you can provide the output here?). next you should check alsamixer on a console. Maybe your master and pcm channels are muted (marked with a MM). Unmute them by pressing 'm'-key.

---

### Post by FarEast on 2006-04-03
Hi lignito;) ,

I know that quite a few people have trouble with the sound chip 'Intel ICH6'.
Here is the link to a thread where you will find your fellows.
[http://www.ubuntuforums.org/showthread.php?t=111870](http://www.ubuntuforums.org/showthread.php?t=111870)

---

