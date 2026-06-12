---
title: "Toshiba X205 Sound Problem"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by José Serra on 2008-03-07
Hello. I have a Toshiba x205-S9349, with a Intel 82801H (ICH8 Family) HD Audio Controller. After I installed gutsy I only get sound from 2 speakers. I'm trying to get to work my 4.1 built in speakers, I have tried several ways with no luck.

Like Here:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
And Here, after this one it seem that sound better but I got no sound from subwoofer:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

There is some way to edit the controls available in alsamixer? Here is a screenshot with all the controls available activated.

---

### Post by LuisGMarine on 2008-03-07
Hey brother how you doing, welcome to the board.  Good news for you is that I followed the same steps, and have the same laptop :)

Here is how to get the sound woofer working.   Type this command into a Terminal window:

```
sudo gedit /etc/modprobe.d/alsa-base
```


Then at the bottom look for a line that says something along these lines :

```
options snd-hda-intel [COLOR="Red"]**model=intel**[/COLOR]
```

If you have the line just edit it so it reads [COLOR="Lime"]**model=toshiba**[/COLOR], if you don't have the line add this whole line to the end of the config file:

[CODE[COLOR="Blue"]]options snd-hda-intel model=toshiba[/COLOR][/CODE]

Reboot your computer and you should now have full sound.  Hope this works for you, by the way this gets your headphone jack to work ,and on I think it makes your mic  port work, haven't tried the mic yet.  Good Luck, hope this works for you.

---

### Post by José Serra on 2008-03-10
Thank you but, that was the first thing I tried when I read this:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller).

In your mixer appears the sound controls for the other channels?

I've enabled backports and my system is up to date. What else should I try?

Just in case this is my  /etc/modprobe.d/alsa-base:

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# options snd-hda-intel probe_mask=8 model=3stack
options snd-hda-intel model=toshiba
```

---

### Post by LuisGMarine on 2008-03-10
You can try recompiling the alsa drivers, here is a guide that provides scripts to do all the hard part for you.  

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

These are the only things I have done to get sound working:

[LIST]
[*]Recompile the Alsa Drivers ( which I just provided the guide for )
[*]Enabled the backports, which you just did
[*]and changed the line in the alsa config file to say " model=toshiba)
[/LIST]

---

### Post by José Serra on 2008-03-11
It doesn't work, I'm starting to think that I must reinstall the entire system... or live without subwoofer. Do you see 4.1 channels in alsa mixer? :-k

---

### Post by Demonfoxkiller on 2008-03-13
hey man, same computer same problem, 26 hours later, this site worked the best adn made it work, follow it to the T
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

thanks to jack_Sparrow for the hours of help

---

