---
title: "VIA Technologies, Inc. VT82C686 AC97 Audio Controller Problems"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by vij26 on 2005-08-01
Hi Everybody, 
I'm new in this forum...
I am using  !Kubuntu! 5.04 and i am having problem with the soundchip: VIA Technologies, Inc. VT82C686 AC97 Audio Controller. It always says something like: soundcard not found... 
How can I make it work? 
Thx in advance!
Vij26

---

### Post by varunus on 2005-08-01
Can you open up a terminal (the konsole) and type "lsmod | grep snd" and post the output here?

Also the output of "lspci' in konsole?

---

### Post by acidtrip on 2005-08-01
Hey I'm having a similar problem aswell, just installed Ubantu last night and can't get the sound working, I also have the VIA AC97 onboard audio chip and I'm not getting any sound at all. I've looked in the device manager, and it is listed there. However when opening a music file for example, it's playing but I'm not getting any sound. It's working fine on my Windows partition so I know it's not a hardware problem. Any advice would be much appreciated, this is my first linux install so I'm still a bit of a n00b with it  :-?

---

### Post by dj_flx on 2005-08-10
I am in a similar aquatic conveyance...

[FONT=Fixedsys]felix@burnserver:~$ lspci | grep -i audio
0000:00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
felix@burnserver:~$

felix@burnserver:~$ lsmod | grep snd
snd_via82xx            25248  3
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  2 snd
felix@burnserver:~$[/FONT]


???

---

