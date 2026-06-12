---
title: "No sound 16.04 integrated laptop speaker"
date: 2017-04-01
forum: Hardware
---

### Post by brownbear on 2017-04-01
I have a Dell XPS 13 9350 Ubuntu edition which I've recently upgraded to 16.04. Currently sound isn't working. 

I tried
```

killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*

```
then
```

pulseaudio -k 

```

then this with reboot
```

killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*

```

then this with reboot
```

do apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

```

then this
```

wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh

```

which created this alsa dump: 
[http://www.alsa-project.org/db/?f=ea37bf0337c37f1f8ded270a2cb8cce112bce103](http://www.alsa-project.org/db/?f=ea37bf0337c37f1f8ded270a2cb8cce112bce103)

Then I ran this. The output is as an attachment.
```

cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; ls -l /usr/share/pulseaudio/alsa-mixer/paths/; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd; find /lib/modules/`uname -r` | grep snd ;cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound > sounddebut.txt

```

Anything else I can try?

---

