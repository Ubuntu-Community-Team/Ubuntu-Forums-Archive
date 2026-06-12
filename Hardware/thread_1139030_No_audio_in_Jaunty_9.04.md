---
title: "No audio in Jaunty 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by SDXeus on 2009-04-26
Hi, I recently removed ubuntu 8.10 from my dual-boot system and then installed ubuntu 9.04 in its place.  So far everything is working great except for my audio.  I get no audio from any of my devices and I have tried messing around with the sound settings, all to no avail.  

.::. my system .::.

HP dv5z-1000 CTO Pavilion Entertainment PC

GNOME:  2.26.1 (Ubuntu 2009-04-14)
Kernel:  2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009)

Audio Devices:  ATI HDMI audio and IDT 92HD71B7X

My primary audio device is the IDT card, and my system is using it with the OSS mixer.  In 8.10 the card was used with the ALSA mixer (I don't know if this is related or not).  When I try to play audio, niether works.

I will greatly appreciate any help and if there is any more information you need to assist me, please ask.

---

### Post by KeeperOfDreams on 2009-04-26
I am adding my information to this too.
Same laptop brand/make/hardware
Pavilion dv5z.
Was working in 8.04 upgraded to 8.10 (never could get wireless to work in 8.10) then to 9.04 (heard my wireless card is better supported, it is)
Everything out of box worked but sound card, suddenly stopped.
Ran init on ALSA and found card was suddenly no longer recognized.
Added module-assistant through apt-get install and hardware now says ok
However sound is still not there.
Not a volume issue, ALSA mixer has all volumes maxed, verified in command and gui, OSS, PULSE, ALSA etc. will not produce sound.  Sound is neither through head jack or speakers.
Installed additional pulse utilities.  Verified those are not muted either and the stream monitor is picking up the software attempting to push the sound.  Still nothing though.
Noticed alsa-base file in etc/modprobe.d is empty, don't know if that's the norm.
Thats what I have for now

---

### Post by SDXeus on 2009-04-27
> **KeeperOfDreams said:**
> I am adding my information to this too.
Same laptop brand/make/hardware
Pavilion dv5z.
Was working in 8.04 upgraded to 8.10 (never could get wireless to work in 8.10) then to 9.04 (heard my wireless card is better supported, it is)
Everything out of box worked but sound card, suddenly stopped.
Ran init on ALSA and found card was suddenly no longer recognized.
Added module-assistant through apt-get install and hardware now says ok
However sound is still not there.
Not a volume issue, ALSA mixer has all volumes maxed, verified in command and gui, OSS, PULSE, ALSA etc. will not produce sound.  Sound is neither through head jack or speakers.
Installed additional pulse utilities.  Verified those are not muted either and the stream monitor is picking up the software attempting to push the sound.  Still nothing though.
Noticed alsa-base file in etc/modprobe.d is empty, don't know if that's the norm.
Thats what I have for now

I concur. I have tried similar steps and still have no audio.

---

### Post by KeeperOfDreams on 2009-04-27
Adding additional information.
Found alsa-base is now alsa-base.conf
pasted alsa-base.conf because when running init it was using alsa-base still for some reason.  Still no result
Added 

options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-m4
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel

to both alsa-base and alsa-base.conf as shown below.
Suddenly PC Speaker beep works, however, still no sound/mic for anything else but PC Speaker sound.

Tried reloading alsa, and removing pulse, still no result. for OSS or ALSA.  Reloaded everything pulse that I had before.

I'll keep you all updated as I search for a solution

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2options snd-pcsp index=-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-m4
options snd slots=snd-hda-intel
# u1Nb.uI7Vp9nVK5B:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel enable_msi=1
options snd-hda-intel model=hp-m4
options snd slots=snd-hda-intel
# u1Nb.uI7Vp9nVK5B:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel

---

### Post by KeeperOfDreams on 2009-04-27
Credits for this go to Gnubian of #alsa at Ubuntu IRC

If your alsa-base file is empty you can copy the datn a from alsa-base.conf
I don't know if that is necessary, but I did.
The add the following

options snd-hda-intel model=ell-m4-2 

at the end of the file

save then reboot

Pulse and OSS work after that. So in your preferences select one of those as desired.

---

### Post by SDXeus on 2009-04-28
> **KeeperOfDreams said:**
> Credits for this go to Gnubian of #alsa at Ubuntu IRC

If your alsa-base file is empty you can copy the datn a from alsa-base.conf
I don't know if that is necessary, but I did.
The add the following

options snd-hda-intel model=ell-m4-2 

at the end of the file

save then reboot

Pulse and OSS work after that. So in your preferences select one of those as desired.

Thanks for the info!

I think I have my issue solved as well. I added the following to the end of my alsa-base.conf file:

```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5 
options snd-hda-intel enable_msi=1
```And once I rebooted my audio started working again!! I have audio from my speakers as well as my headphones. I didn't have an alsa-base file though, just the alsa-base.conf file.

Also, here is what the entirety of my alsa-base.conf file looks like:
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
```


Thanks for your help! Wouldn't have gotten it working without your help.

---

### Post by Themotorman on 2009-05-24
I found that the speaker icon open up a slider panel and that my PCM slider was set to zero ...that's all it took to get back the "lost" audio.
Hope this works for others... I still cannot get the pulseaudio to work on capture.. but Skype works and also everything else so ...
Thanks everyone for your ideas. Ron says: "life is short, download Ubuntu first!!":p:p:p

---

### Post by migueletorres on 2009-05-29
I'm sorry, but I'm a newby could you pleass telme where can I find the files? (i.e. detail a little bit the process)


Thank you!

---

### Post by KeeperOfDreams on 2009-05-30
Miguel, if you work for Rockwell Automation Engineering Support, come see me at work...  D114.  

Otherwise
sudo gedit etc/modprobe.d/alsabase.conf

add 

options snd-hda-intel model=ell-m4-2 

to the bottom of the file and save, reboot

I found Pulse Audio is drops and locks up on these PCs too, so I went to 

[Ubuntu 9.04 Jaunty &#8211; Keeping the beast Pulseaudio at bay « Tux&#8217;s idyllic life.]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") 

To remove enough of Pulse to use ALSA if Pulse gives you pains.

---

### Post by mikenz on 2009-05-30
hi there i have a problem with my hp dv5 not having any sound on ubuntu 9.04
i have open the file sudo gedit etc/modprobe.d/alsabase.conf and that is empty so i read the last post and went to proceed with sudo gedit etc/modprobe.d/alsa-base.conf
and that was empty aswell what am i doing wrong. can anyone help me out im new to ubuntu thank you very much.

---

### Post by Yellow Pasque on 2009-05-30
Copy and paste:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

---

