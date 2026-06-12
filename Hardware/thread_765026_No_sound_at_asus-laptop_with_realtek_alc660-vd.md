---
title: "No sound at asus-laptop with realtek alc660-vd"
date: 2008-04-24
forum: Hardware
---

### Post by deivid85 on 2008-04-24
Hi everybody!

After several days which i've tried to resolve my problem with the sound in my laptop i've decided write us.

I've installed Ubuntu 7.10. Because of the sound don't play I installed ALSA 1.0.16 and then, it recognized the card and said that installed it correctly, however, the sound is off.
I've followed the steps at URL: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and read a lot of webs with diferents solutions but I can't resolve the problem.

> I run alsamixer and there aren't channels muted.
> I've installed alsaconf many times and nothing.
> I've read the ubuntu guide.
> Only get sound adding the line "options snd-hda-intel model=lenovo" at the end of the file /etc/modprobe.d/alsa-base but this produced a deafening sound.

Please, help me.

Thanks!!

---

### Post by deivid85 on 2008-04-24
My sound system information is:

alsamixer:
Card: HDA Intel
Chip: Realtek ALC-660VD

lspci:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

lsmod | grep snd:
snd_hda_intel         261144  1 
snd_pcm_oss            43392  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                77960  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4100  0 
snd_seq_oss            33920  0 
snd_seq_midi            8832  0 
snd_rawmidi            25088  1 snd_seq_midi
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                51440  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23044  2 snd_pcm,snd_seq
snd_seq_device          8844  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10376  2 snd_hda_intel,snd_pcm

cat /proc/asound/card0/codec#* | grep Codec:
Codec: Realtek ALC660-VD
Codec: Motorola Si3054 


If you need more information ask me.

---

### Post by jocko on 2008-04-24
> **deivid85 said:**
> 
> Only get sound adding the line "options snd-hda-intel model=lenovo" at the end of the file /etc/modprobe.d/alsa-base but this produced a deafening sound.

A very high pitch squeeling noise? Could it be feedback between your speakers and microphone?
Try muting your microphone in alsamixer and try again.

---

### Post by sleepydada on 2008-06-04
I have the similar problem. Help!!

---

### Post by CarlesOriol on 2008-06-06
Also I'm on the same problem on an Asus x20sgseries with the same alc660-vd.

---

### Post by Yellow Pasque on 2008-06-06
ALSA 1.0.17-rc1 came out today. Make sure to configure the alsa-base file appropriately.
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by CarlesOriol on 2008-06-07
After thousand tests using ALSA 1.0.17-rc1 and all possible combination flags in modprobe it still NOT working on my asus x20sg.

It looks like the card it's ok but there's something muting the sound. (may be it's some motherboard flag?)

---

### Post by CarlesOriol on 2008-06-07
At last I did it.

I build the drivers as tells Temüjin. ([http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959))

After I've add to **/etc/moprobe.d/alsabase**

**options snd-hda-intel model=lenovo**

and it worked.

Thanks

---

### Post by Yellow Pasque on 2008-06-09
CarlesOriol, thanks for the feedback; I added your model to the list. Enjoy your sound!

---

### Post by msegmx on 2008-06-19
hello,
my laptop is asus m51s with realtek alc660-vd.

after adding the line :

options snd-hda-intel model=hp

i got sound. but when i plugin a headphone i get no sound anymore (neither through headphones nor laptop itself). after unplugging the headphone there's sound again. 

i can record sound through sound recorder and the same headphone mic.

at system start, bios plays a short melodi which i'm able to hear through the (still plugged in) headphones. so the headphone is working.

no sound is muted in alsamixer.

can anybody help ?
do you guys have sound on headphone ?

thanks in advance

---

### Post by PabloSCasas on 2008-08-02
My laptop is Asus U1E with realtek alc660-vd. After many many readings of posts and searches, sound MIRACLELY worked by simply adding the line:
 
 options snd-hda-intel model=lenovo

to /etc/modprobe.conf (I use Mandriva 2008.1). I'm very happy!!

---

### Post by edwardchuajh on 2008-08-03
Msegmx,

I have the same laptop and problemas you, and spent a week going through forums trying to get my headphones to work =P

then i stumbled upon this post #12 here [http://ubuntuforums.org/showthread.php?t=820959&page=2](http://ubuntuforums.org/showthread.php?t=820959&page=2) apparently our headphones are by default muted.

though there isn't an option in **alsa-mixer**, just try going into your terminal and run **alsaunmute**.

It worked for me and the headphones are working great now =)

let me know if it helped =)

ASUS M51Sn.. *slurp* =)

---

### Post by Newton Lame on 2008-08-04
> **PabloSCasas said:**
> My laptop is Asus U1E with realtek alc660-vd. After many many readings of posts and searches, sound MIRACLELY worked by simply adding the line:
 
 options snd-hda-intel model=lenovo

to /etc/modprobe.conf (I use Mandriva 2008.1). I'm very happy!!

PabloSCasas!
You may be my man! I have just bought U1E, and i also would like to run a Linux, preferably Ubuntu on it.
But i am a complete newbie, i need some more specific help, and not only with the sound.

Let me ask first, did you just simply added that line to the file's end? I'm going to test it with Wubi today.

Other: how did you manage with the 16:9 (1366x768) screen? Ubuntu messed it up for me. The login screen and panels were only 1024 wide.

You can also e-mail me on(jzmail AT freemail DOT hu), as the others may not be interested in these specific issues.

Thanks!

---

### Post by sayad on 2008-08-04
wellit is not that unawaiting that a new product might be disturbance free.I have bought acer laptop but also i have my 1 year replace wraenty , thats why i get to change the rom drive.If you have the warenty too , you change the spekaers too .never thee les ask your vendor for assistance.afterall - theey are kepng 4% warenty charge !!!

---

### Post by Jack the R on 2008-08-13
Hopefully it's not too late to get advice on this - 

I've followed [_these_](http://ubuntuforums.org/showthread.php?t=820959) instructions for installing ALSA 1.0.17, and set the option 

options snd-hda-intel model=lenovo

in /etc/modprobe.conf.  Rebooted, ran alsamixer, got this - 

[img]http://www.extinctionlevelevent.com/misc/linux/no_headphones.png[/img]

What gives?

I'm on an Asus R1E tablet.

---

### Post by Jack the R on 2008-08-14
Sure wish someone would help with this . . .

---

### Post by Jack the R on 2008-08-15
Solved it - headphones work with
 
options snd-hda-intel model=asus

and 

options snd-hda-intel model=auto

although alsa mixer shows the same lack of volume controls as above.  The regular GUI volume slider works.

---

### Post by sig_ on 2008-09-17
I have a realtek alc660-vd, or Intel ICH8.

Here's my alsa-info: [http://www.alsa-project.org/db/?f=fcd673ad741649894a2e0995bac67cd7ab64e1e9](http://www.alsa-project.org/db/?f=fcd673ad741649894a2e0995bac67cd7ab64e1e9)

adding model=lenovo to /etc/modprobe.d/alsa-base didn't solve my problem...

---

### Post by l0co on 2009-11-15
Last weekend I spent about 6 hours to get the sound on ASUS laptop with Hardy (this time it's F5GL model, but I believe that all asus-related sound problems are related :) ). 

I read hundreds of threads and I tried a lot of solutions. None of them worked (including setting various models for snd-hda-intels in alsa-base, which were the simpliest solutions I tried).

Finally I've found the one working solution for me - remove ALSA and use the OSS, what is desribed here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Now sound works without any problems. Attention for Hardy users - don't remove alsa-utils package, because this package has gdm in depencences, and removing it will remove gdm. Remove only alsa-base and blacklist all alsa modules.

Hope it helps.

---

