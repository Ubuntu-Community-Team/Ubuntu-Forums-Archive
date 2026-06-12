---
title: "Audio Issue (hp mini note 1000)  (STAC92xx chipset)"
date: 2008-11-29
forum: Hardware
---

### Post by kaffaman on 2008-11-29
Hey, guys. I too run Ubuntu 8.10 on HP mini 1000 (STAC92xx audio). Instead of running usual install, i chose alternate CD (command line system), then installed Xorg, wmii and so on. Problem == sound. 
 
When tying to play music / test speakers  i get no errors, but so sound either. 

Yeah, i tweaked/searched a lot ;0)

Here is some info: 

uname -a : 
   Linux mini 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686

1)  options snd-hda-intel model=ref IS added to /etc/modprobe.d/alsa-base

2)  output of "aplay -l" 
    card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
     Subdevices: 1/1
     Subdevice #0: subdevice #0
--- should there be "device 0" [STAC92xx Digital] (used to have it before)

3) alsamixer/alsamixergui used to set Master & PCM, nothing is (MM) muted

4) No errors from   "/etc/init.d/alsasound restart" : 
     Shutting down sound driver: done
     Starting sound driver: snd-hda-intel done

5) Output of /etc/init.d/alsa-utils restart  :
 * Shutting down ALSA...                  [ OK ] 
 * Setting up ALSA...                     [ OK ]

6) Output of " lsmod | grep snd " 
   snd_hda_intel         428308  0 
   snd_pcm_oss            46496  0 
   snd_mixer_oss          22912  1 snd_pcm_oss
   snd_pcm                83844  2 snd_hda_intel,snd_pcm_oss
   snd_hwdep              15492  1 snd_hda_intel
   snd_seq_oss            39936  0 
   snd_seq_midi_event     15232  1 snd_seq_oss
   snd_seq                58480  4 snd_seq_oss,snd_seq_midi_event
   snd_timer              29448  2 snd_pcm,snd_seq
   snd_seq_device         15500  2 snd_seq_oss,snd_seq
   snd                    66212  9        snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16776  2 snd_hda_intel,snd_pcm

7) Did try compiling by hand (alsa-driver-1.0.18, alsa-lib-1.0.18, alsa-utils-1.0.18) & running alsaconf, and ./snddevices (makes /dev/snd*) 

8) cat   /etc/rc.local   : 
   rmmod snd_hda_intel
   modprobe snd_hda_intel
   exit 0

9) cat /etc/modprobe.d/sound   : 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

10) Here is the list of installed stuff: aptitude search '~i' | grep alsa
   alsa-base                    
   alsa-oss                        
   alsa-source                
   alsa-tools-gui                  
   alsa-utils                                                  
   alsamixergui                   
   libesd-alsa0                   
   libsdl1.2debian-alsa           

11) cat /etc/modules : 
   loop
   lp
   fuse

12)  cat /etc/modprobe.d/sound 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel


Thanks for your help!

---

### Post by kaffaman on 2008-12-04
Well, since there is not much input, here is the solution that I worked out myself

download and compile: 
alsa-driver-1.0.18.tar.bz2

with ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r) && make && make install 


then: 
alsa-lib-1.0.18.tar.bz2
alsa-utils-1.0.18.tar.bz2

with simpe ./configure && make && make install 

Make sure that 

/etc/modprobe.d/alsa-base

Has line: 
options snd-hda-intel model=ref

Fire up alsamixer and make sure the PCM, Master, Front etc are turned up.

---

### Post by silvari on 2009-03-22
Thanks for posting this, found it VERY helpful for getting audio working out of the headphone/mic jack on my 1030NR.

Similar details here:
[https://answers.launchpad.net/ubuntu/+source/linux/+question/57848](https://answers.launchpad.net/ubuntu/+source/linux/+question/57848)

---

### Post by Ubuntiac on 2009-03-30
Gohai reported getting his to work with the newer 1.0.19 ALSA driver. There's a PPA listed for it at the end of [this big report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/"). (Subscribe and choose "This bug affects me" up the top while you're there).

---

### Post by kennethmsmith on 2009-07-22
Hey.. Silvari ... I have 1030NR also... get sound through my headphone jack, but my speakers aren't working.  Know a fix for this?  Plus the volume (even when turned all the way up) seems kinda low.  Help please.  Thanks.

---

