---
title: "How to reinstall sound driver?"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by tw33ty74 on 2009-06-19
Hi, i'm using ubuntu 9.04 with M-Audio audiophil 24/96 sound card. When I first install ubuntu 9.04 everythings works fine. Even the sound card. But after the latest patches, my sound card doesn't work anymore.
 
Can Someone tells me how to reinstall the sound driver?
 
Thanks
 
tw33ty74

---

### Post by Brendan.Johnston on 2009-06-22
I am using the on board Intel sound and optical S/PDIF ([http://en.wikipedia.org/wiki/SPDIF](http://en.wikipedia.org/wiki/SPDIF)).  This stopped working yesterday.  I would like to reinstall/config the sound drivers also and don't know how.

---

### Post by tommcd on 2009-06-22
To find out what sound chipset your sound card uses, open a terminal (applications > accessories > terminal) and run:
```
lspci | grep -i audio
```
Then to find the modules used by your sound card, run:
```
lsmod | grep -i snd
```
Post the output of both of those commands here. Also please post the exact model number of your sound card if you know it.

And welcome to the Ubuntu forums!

---

### Post by harrypottergw on 2009-06-22
Hi, this is what i got for both of the commands. I cannot have ANY sound come out of my netbook. mine is a Toshiba nb205 with ubuntu netbook remix 9.05

   william@william-laptop:~$ lspci | grep -i audio
  
  00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
  
  

william@william-laptop:~$ lsmod | grep -i snd
  
  snd_cs4236             22924  0 
  
  snd_opl3_lib           18560  1 snd_cs4236
  
  snd_hwdep              15108  1 snd_opl3_lib
  
  snd_cs4236_lib         22656  1 snd_cs4236
  
  snd_wss_lib            33920  2 snd_cs4236,snd_cs4236_lib
  
  snd_mpu401_uart        15104  1 snd_cs4236
  
  snd_hda_intel         434100  3 
  
  snd_pcm_oss            46336  0 
  
  snd_mixer_oss          22656  1 snd_pcm_oss
  
  snd_pcm                82948  4 snd_cs4236_lib,snd_wss_lib,snd_hda_intel,snd_pcm_oss
  
  snd_seq_dummy          10756  0 
  
  snd_seq_oss            37760  0 
  
  snd_seq_midi           14336  0 
  
  snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
  
  snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
  
  snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  
  snd_timer              29704  4 snd_opl3_lib,snd_wss_lib,snd_pcm,snd_seq
  
  snd_seq_device         14988  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  
  snd                    62628  21 snd_cs4236,snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_wss_lib,snd_mpu401_uart,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
  
  soundcore              15200  1 snd
  
  [FONT=&quot]snd_page_alloc         16904  3 snd_wss_lib,snd_hda_intel,snd_pcm[/FONT]

thanks

---

### Post by tommcd on 2009-06-23
Did you have any luck working your way through the sound troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Your laptop uses the **snd_hda_intel** driver, which your **lsmod** shows is already running. First, try opening **alsamixer** in the terminal and turn all the volume levels up. Hot the **Esc** key twice to exit alsamixer. Also, open the sound preferences GUI on the desktop and select alsa instead of pulse audio. I'm not sure if Ubuntu netbook remix uses pulse audio or not.

---

### Post by Brendan.Johnston on 2009-06-23
For me the values returned are:

johnbre@media:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
07:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
07:00.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
07:00.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
07:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
07:01.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
07:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
johnbre@media:~$ lsmod | grep snd
snd_hda_intel         435636  2 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_pcm                82948  3 snd_hda_intel,cx88_alsa,snd_pcm_oss
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  18 snd_hda_intel,snd_seq_oss,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
johnbre@media:~$

---

