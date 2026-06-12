---
title: "tv-tuner doesn't work anymore"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by subjectdenied on 2004-10-12
my WinTV tv-card doesn't work anymore

since some days ago and some apt updating, my tv card refuses to work. however it is detected and installed, the problem seems to be with not detecting any channels. do i have to set some parameters for the bttv-kernelmodule?

i tried xawtv and tvtime with no success

---

### Post by clark3rd on 2004-10-16
I've never been able to get my TV card working with the 2.6 kernel. In 2.4, I know how to hack the modules.conf file to make it work, but I'm lost with 2.6. Here's my problem, from dmesg:

bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
bttv0: using tuner=5


The card is id'ed correctly, it's the tuner that is wrong (should be 2). 

Any ideas would be fantastic. Anyone?

---

### Post by badriram on 2004-10-17
[quote=clark3rd]I've never been able to get my TV card working with the 2.6 kernel. In 2.4, I know how to hack the modules.conf file to make it work, but I'm lost with 2.6. Here's my problem, from dmesg:

bttv0: detected: Leadtek WinFast TV 2000 [card=34], PCI subsystem ID is 107d:6606
bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
bttv0: using tuner=5


The card is id'ed correctly, it's the tuner that is wrong (should be 2). 

Any ideas would be fantastic. Anyone?[/quote]

Try adding a file with the following line into the /etc/modprobe.d folder

options bttv card=34 tuner=2

---

### Post by subjectdenied on 2004-10-19
i was able to solve my problem!

the tuner module that gets loaded at startup is set to "2" by default, which seems not to be the right value for my card

by using the "dmesg" command to read the messages given by the bttv-module, and reloading the bttv module i found that the right value for my tuner would be "5"

as suggested above i added a file with the following settings to my /etc/modprobe.d directory

```
options bttv tuner=5
```

now its working again , anyway i think that this could be a bug, because the problem appeared after apt-getting some updates for the preview version released some weeks ago, which did set the correct tuner-value for my card

thanks for your help

---

### Post by dikki on 2005-03-05
I have a Leadtek Winfast TV2000 XP, too; and I'm using Warty. 

I read the topics about tvtuners, but it's not clear to me, what to do. Somewhere the solution is to put a file with "options bttv card=34 tuner=2" to /etc/modprobe.d ; in an other topic is to write "bttv card=34 tuner=2" to /etc/modules . For somebody tuner=5 works, and for an other guy tuner=2 is the right value.

Everybody gets clear messages with "dmesg", I got this:

```
: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff4 [stereo/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe8 [stereo/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe0 [stereo/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe0 [stereo/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe8 [stereo/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe0 [stereo/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe0 [stereo/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff4 [stereo/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe0 [stereo/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff4 [stereo/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xffe6 [mono/pilot c1] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_AUTO_STEREO
cx8800[0]: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_AUTO_STEREO

``` 


Anybody who has a Winfast TV2000 XP, solved the problem, could help me?

What I did: installed Warty - the tvtuner appers in the device manager, and seems to be ok; installed tvtime; scanned for channels. What's wrong: the picture is only black&white, and there's no sound.

---

