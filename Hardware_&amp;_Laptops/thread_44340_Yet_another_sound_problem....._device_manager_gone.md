---
title: "Yet another sound problem...../ device manager gone mad"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by Akis on 2005-06-25
Here is my problem, in my Hp laptop i have an [COLOR=Navy]ADI(Analog Devices) 1981B[/COLOR] sound card, but instead of that my ubuntu's device manager is claiming these:

> 
vendor; ATI Techologies INC.                          (!)
device: IXP 150 AC'97 Audio Controler           (totally inaccurate)

Status: Status                                                (???)

Device: Unknown                                            ( :-P )
Capabilities: Unknown
 

[COLOR=Navy](i didnt know that now ATI makes sound cards as well !!!!!!! )[/COLOR]

thats what i get with the [COLOR=Red]sudo lsmod |grep snd*[/COLOR]:

snd_atiixp             19880  0
snd_ac97_codec         59268  1 snd_atiixp
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_atiixp,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc         11144  2 snd_atiixp,snd_pcm

i dont know if it really matters but this command [COLOR=Red]lsof /dev/dsp[/COLOR]  gives back this error:


lsof: status error on /dev/dsp: No such file or directory
lsof 4.71
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRstUvV] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+|-M] [-o [o]] [-p s]
 [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.

if you have any idea on how to fix these or on how  i can correct the sound card model plz help!!!!

---

