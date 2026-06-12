---
title: "Sound Card Issue after connecting to TV"
date: 2018-06-27
forum: Hardware
---

### Post by J_Templeton on 2018-06-27
I recently bought a computer from Think Penguin and a TV to use as a monitor.  The TV didn't work out and I went back to my old monitor.  I think that because I connected with an HDMI cable when I first booted up, the sound card was configured for the internal speakers/HDMI ARC.  Now, I can't get sound with my speakers through line out.  I was able to for awhile, after restarting pulse audio, but suddenly not even that works.  I tried a few things to resolve the issue but no luck.  Is there a way to reset the sound profile altogether?  I might call Think Penguin for support, but thought I would ask here first.  When I use the volume buttons on my keyboard it shows "Digital Output (S/PDIF)" if that is any help.  I am longtime Ubuntu/Linux user but have been using an all-in-one the past few years with built in speakers and didn't have any issues with sound.  I am usually pretty good at searching for resolutions online, but most of them seem to be the opposite problem than the one I'm having.

---

### Post by Yellow Pasque on 2018-06-28
Tried this?
```
rm -r ~/.config/pulse; pulseaudio -k
```

---

### Post by J_Templeton on 2018-06-28
I did, and just to be certain tried it again.  I also tried this this morning: [https://askubuntu.com/questions/1029502/ubuntu-18-04-no-audio/1030811](https://askubuntu.com/questions/1029502/ubuntu-18-04-no-audio/1030811)  I can't seem to change the port with Pavucontrol, so that was a no go.  And suddenly, I can't even connect to a Bluetooth speaker, which was working fine until that last step.

---

### Post by J_Templeton on 2018-06-28
Also, I don't think this is a hardware issue, given this has been a problem for multiple users.

---

### Post by J_Templeton on 2018-06-28
Update: I just tried this from the Troubleshooting Guide

```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`



```

I got an error that /home/.pulse* doesn't exist.  So now I am trying to figure out how to install pulseaudio . . .

---

### Post by Yellow Pasque on 2018-06-28
This command is very outdated. ~/.pulse was changed to ~/.config/pulse several years ago.
```
rm -r ~/.pulse*
```

> So now I am trying to figure out how to install pulseaudio . . . 

Did you uninstall it? Not sure what you're talking about...

---

### Post by J_Templeton on 2018-06-28
I think that perhaps one of the things I tried removed it, and I did reinstall it, but still no sound.

---

### Post by Yellow Pasque on 2018-06-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Maybe this will help too: 
```
pacmd list-sinks
```

---

### Post by J_Templeton on 2018-06-29
I blacklisted HDMI with this:

```
sudo sh -c "echo 'blacklist snd_hdmi_lpe_audio' > /etc/modprobe.d/blacklist-snd-hdmi-lpe-audio.conf"
```

Worked like a charm!

---

