---
title: "Intel sound card works in Gutsy but not in Hardy"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by macroshaft on 2008-02-04
I have an Acer aspire 5315, I've had all the usual problems, wifi, compiz etc and solved them under Gutsy. The sound didn't work but the fix was to turn on backports and reboot. LSPCI reports the sound card as:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Having dist-upgraded to Hardy alpha 3 I found everything works except the sound. I tried removing and re-installing the backports but it now states:

linux-backports-modules-2.6.22-14-generic:

Package linux-backports-modules-2.6.22-14-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Any ideas? Is this a bug? or is this how it's supposed to be during testing?

---

### Post by ubuntel on 2008-02-22
hi 
i am having the same problem after upgrading to hardy 
> laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
 lspci -vv | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

i did run alsamixer everything is unmuted and looks normal

---

### Post by ubuntel on 2008-03-04
whatever upgrades i did yesterday my sound is finally working :guitar:

---

### Post by hithwen on 2008-04-25
I've just upgraded to Hardy and my sound isnt working either :'(

```
$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

Wow, It's fixed!
I followed the instructions[ here]("http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/"):
```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo /etc/init.d/alsa-utils reset

```

---

### Post by happyisland on 2008-04-26
Wow! That fixed my problems with Hardy sound too. I also have the ALC883 chip, and the fix worked perfectly. 
Thanks!

---

### Post by emerald2dragon on 2008-05-04
Hey, i was careful when upgrading my 7.10 to 8.4

If you edited the ath_pci (or whatever the file was, sorry i cant remember) that made it detect your sound and it was working fine with 7.10, when it installed 8.4 it said "do you want to keep or replace these edited files?" and they were the ones that i had edited to get my wireless and sound working.

so in short, if you had them replaced you'll just have to edit them again, but i kept mine and they still work.

hopefully thats some help to people ^_^

---

