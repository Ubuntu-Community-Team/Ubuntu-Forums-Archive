---
title: "Sound on Inspiron 3500 - update help for 9.04"
date: 2009-07-27
forum: Hardware
---

### Post by marklar2u on 2009-07-27
Can someone please help me get this updated for 9.04?

solved for previous kernels here: [http://ubuntuforums.org/showthread.php?t=284405](http://ubuntuforums.org/showthread.php?t=284405)

Apparently this issue was solved for earlier versions but I've failed with a few attempts, including adapting the old instructions as listed below (oh, and BIOS was set to soundcard = Auto):

1) deleted /etc/modprobe.d/alsa-base

2) I deleted the "blacklist sb" line from /etc/modprobe.d/blacklist-oss file

3) I created /etc/modprobe.d/inspiron3500snd.conf

which is composed of the stanzas posted by Pianoman72:

Code:

blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8



** wondering, in these stanzas  do I need to add ".conf" to some names???  do I need to keep the file in step 1?  

thanks!

---

### Post by marklar2u on 2009-07-27
apparently, this is already known, and reported by one of the lead folks from the thread referenced in the first post...any ideas would be appreciated...thanks.

see his followup that the prior workaround / fix stopped working here:  

[http://ubuntuforums.org/showthread.php?t=1073370&highlight=inspiron+3500](http://ubuntuforums.org/showthread.php?t=1073370&highlight=inspiron+3500)

---

### Post by Pianoman72 on 2009-07-28
Hey poor Dell Inspiron 3500 users,

I have returned and I will make an attempt to get the sound working again.

I will probably install Xubuntu 9.04, though.  I'm assuming it handles sound in the same way that Ubuntu does?

I think that mine is still on 7.x.

Any error messages or clues as to what the problem may be?  I'm assuming that the sound hardware is not recognized or initialized.

---

### Post by Pianoman72 on 2009-07-29
Assuming a fresh install of 9.04,

The first thing you need to do (the last thing I tried) is to add yourself to the audio group.

```
sudo adduser your_username audio
```

(this requires restart)

Next, blacklist the usual suspects.  Add these lines to /etc/modprobe.d/blacklist.conf
```
blacklist snd-opl3sa2
blacklist snd-nm256
```

Then, edit /etc/modules
From the /etc/ dir:
```
sudo pico modules
```
I added:
```
snd-sb8 irq=5 port=0x220 dma8=1
snd-mixer-oss
snd-pcm-oss
```

Now you need to create a config file for the snd-sb8 module
Name it snd-sb8.conf and create it in /etc/modprobe.d

Here is mine:

```
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-sb8
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1
```

I know this is probably more effort than needed, but my soundcard is working.

---

