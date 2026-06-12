---
title: "Audio Sound Output Stops - Ubunto 20.04, X570 motherboard ALC887 Audio"
date: 2021-02-10
forum: Hardware
---

### Post by dwoolridge on 2021-02-10
Hello,

I've been Googling for 3 days now trying to resolve this issue and am at my wit's end...  Any help with this issue would be most appreciated!

On fresh boot, I can use "aplay hello.wav" to play a file.  Usually it will work multiple times.  After playing audio between 2 to 5 times, aplay will stop working and do one of 2 things:

[LIST=1]
[*]Respond with-->  aplay: main:830: audio open error: Device or resource busy
[*]Respond with the following and just sit there (no sound)--> Playing WAVE 'hello.wav' : Signed 16 bit Little Endian, Rate 16000 Hz, Mono
[/LIST]

Ubuntu 20.04
Gigabyte X570 UD motherboard
  ALC887 audio
AMD Ryzen 7 3700X processor

Here's a summary of some of the many things I've tried...
>  
    Originally, there was no sound at all..

sudo install ffmpeg
     sudo apt install ubuntu-restricted-extras

     sudo apt-get install --reinstall alsa-base pulseaudio
     sudo alsa force-reload
     reboot

     killall pulseaudio; pulseaudio -k  ; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*
     pulseaudio --start

     sudo apt install --install-recommends linux-generic
     ubuntu-drivers list  [note the level  nvidia-340]
     sudo apt install --install-recommends linux-modules-nvidia-340-generic 
     reboot

SOUND STARTED WORKING HERE, BUT WOULD STOP AFTER BEING USED A FEW TIMES

     sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm3 ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm3 ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status || ubuntu-security-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
     reboot

     TROUBLESHOOTING
     aplay -l
     aplay -L
     lsmod | grep snd
     pactl list short sinks
     alsamixer
     amixeer scontrols
     lspci -nn

pavucontrol   [in the GUI]

lspci -nn   
09:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be4] (rev a1)
0b:00.4 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Starship/Matisse HD Audio Controller [1022:1487]

Create / Edit  /etc/modprobe.d/default.conf
     add:  options snd_hda_intel index=1

edit /etc/pulse/client.conf:  change to autospawn = no   [from ; autospawn = yes]

     sudo apt-get install --reinstall alsa-base pulseaudio
     sudo alsa force-reload
     sudo killall pulseaudio; pulseaudio -k  ; rm -r ~/.config/pulse/*
     reboot
     pulseaudio --start

     Worked once, now??  NOPE

     sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
     sudo apt-get update
     sudo apt-get install linux-image-extra-`uname -r`
     sudo apt-get install --reinstall linux-image-extra-`uname -r`  
     sudo apt-get install oem-audio-hda-daily-dkms
      [Above set of commands failed]

     Make the "HD-Audio Generic" device default:
      aplay -l
          [Output...]
          **** List of PLAYBACK Hardware Devices ****
          card 0: Generic [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
            Subdevices: 0/1
            Subdevice #0: subdevice #0
          card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
            Subdevices: 1/1
            Subdevice #0: subdevice #0
          card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
            Subdevices: 1/1
            Subdevice #0: subdevice #0
          card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
            Subdevices: 1/1
            Subdevice #0: subdevice #0
          card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
            Subdevices: 1/1
            Subdevice #0: subdevice #0
      
[Edit/Create  /etc/asound.conf]
        pcm.!default {
  type plug slave.pcm {
    type hw card 0 device 0
  }
        }

      [Add the following to  /etc/modprobe.d/alsa-base.conf]
        options snd-hda-intel model=auto   
[Then tried]
        options snd-hda-intel model=generic

      [Edit /usr/share/pulseaudio/alsa-mixer/paths/analog-output-lineout.conf]
        From:
  [Element Desktop Speaker]
  switch = off 
  volume = off
To:
  [Element Desktop Speaker]
  switch = on
  volume = on


---

