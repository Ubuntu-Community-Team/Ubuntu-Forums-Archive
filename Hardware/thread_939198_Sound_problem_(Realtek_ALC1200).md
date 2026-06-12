---
title: "Sound problem (Realtek ALC1200)"
date: 2008-10-05
forum: Hardware
---

### Post by jesper1266 on 2008-10-05
I'm having problems getting sound to work on my Asus P5Q-EM motherboard. The onboard sound chip is a ALC1200 chip from Realtek. There is no sound at all in neither the front or back minijack connector. I've tried both ubuntu 8.4 and 8.10 beta.

There seems to be something wrong with the detection of the sound chip as the sound configuration (System->Preferences->Sound) has it noted as a ALC888 chip. Furthermore if i execute a lspci in a terminal, the resulting information tells that the sound chip is:

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


Can anyone help me?

---

### Post by redDEADresolve on 2008-10-05
I recently purchased an Asus P5Q-EM, everything is working relatively well except for sound. I have a Realtek ALC1200, 8 channel audio chipset and cannot get audio to work in Ubuntu 8.10 Beta.

lspci also outputs
Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

and the volume manager is reconditioning my audio as a ALC888

Any help would be appreciated. Thanks!

---

### Post by jesper1266 on 2008-10-06
Hi redDEADresolve,

What version of the bios are you running?

I've tried setting the soundcard to AC97, this results in 8.10 hanging during boot, so this is not the solution.

Cheers Jesper

---

### Post by jesper1266 on 2008-10-06
I've tried installing the newest drivers from Realtek's homepage (5.07) the alsa utils that follows the drivers is unable to find the soundcard.

Bummer!

---

### Post by markbuntu on 2008-10-06
Did you go to the alsa site to see if this is supported yet?

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by redDEADresolve on 2008-10-07
I just updated to P5Q-EM BIOS 0402 (the 09/05/08 release).

I checked the ALSA wiki and didn't see any mention of my soundcard.

Any help is still appreciated.

---

### Post by lrc3 on 2008-10-08
I have ASUS P5Q-EM too. I installed KUbuntu intrepid beta with the latest daily update.

I *can hear* the login sound, but

when i play mp3 file, the player (Aamok) seems going fine, just *no sound* coming out from the jack.

I *guess* the device is still in-use?

---

### Post by redDEADresolve on 2008-10-08
> **lrc3 said:**
> I have ASUS P5Q-EM too. I installed KUbuntu intrepid beta with the latest daily update.

I *can hear* the login sound, but

when i play mp3 file, the player (Aamok) seems going fine, just *no sound* coming out from the jack.

I *guess* the device is still in-use?

When I open Amarok it tell me no audio device has been initialized.

---

### Post by lrc3 on 2008-10-08
Nevermind, I got sound *working* on ASUS P5Q-EM / KUbuntu 8.10

For some reason, The PCM channel in KMix is muted after installation. I pretty sure I didn't do it.

Is my device different than yours?
lso@lso-dev1:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


I still can't get my X working with Accelerate option.

---

### Post by redDEADresolve on 2008-10-08
> **lrc3 said:**
> Nevermind, I got sound *working* on ASUS P5Q-EM / KUbuntu 8.10

For some reason, The PCM channel in KMix is muted after installation. I pretty sure I didn't do it.

Is my device different than yours?
lso@lso-dev1:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


I still can't get my X working with Accelerate option.

red@red-desktop:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

Same Card, same board, no sound

---

### Post by jesper1266 on 2008-10-09
lrc3 could you tell us about the hardware in your system? Bios version and so forth?

Have you tried the straight ubuntu installation (not Kubuntu)?

Cheers

Jesper

---

### Post by jesper1266 on 2008-10-09
I've just installed kubuntu 8.10 beta. And the Sound does not work out of the box, can you tell us, how you did it?

Thanks

Jesper

---

### Post by lrc3 on 2008-10-11
My system:
ASUS P5Q-EM
Intel E8400
Adata 2x2GB PC2-6400
One Seagate 500GB Harddrive
No CD-ROM
BIOS version 0202 -> 0402 ( I did it on 7 days ago for not good reason. on both version, Sound works for me, After upgrade Vista doesn't regonize my LAN card )
KUbuntu 8.10 beta 32-bit with the latest daily update
Kernel-generic 2.6.27 -4 to 2.6.27-7 all works for me. 
I install Kenrel-server 2.6.27-7 yesterday and everything still working, because I need 4GB RAM supported in 32-bit OS.

lso@lso-dev1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lso@lso-dev1:~$

lso@lso-dev1:~$ sudo cat /proc/asound/card0/codec# | grep Code
cat: /proc/asound/card0/codec#: No such file or directory


I also got RealPlayer11.05 installed btw.

---

### Post by Ragnarök on 2008-10-12
Have you try with executing alxamixer from console and putting  all the levels to the top?

It works for me.

I have:

victor@victor:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by jesper1266 on 2008-10-18
Unfortunantly this did not work for me. The alasmixer runs fine in the terminal, but the system is unable to initialize the soundcard.

I've tried updating to version 1406 of the bios, that didn't help.

Cheers
Jesper

---

### Post by redDEADresolve on 2008-10-19
after the today's kernel update, 10.19.08 my sound is working

---

### Post by jesper1266 on 2008-10-26
Hi,

Have you made any changes in the bios to make it work? 

Cheers 

Jesper

---

### Post by redDEADresolve on 2008-10-26
No I updated my system and took out my Nvidia card.

Nvidia cards are messing with sound in Ubuntu 8.10

---

### Post by jesper1266 on 2008-11-02
Confirmed:

Removing my NVIDIA 9600 GT graphics card from the PCIE port, and using the onboard graphics card, enabled the sound under Ubuntu 8.10.

This must be a bug!
Does anybody know how to get around this problem? I need the graphics card in order to run 3D aplications under ubuntu.

Cheers

Jesper

---

### Post by fifthconspiracy on 2008-11-04
With updates for 8.10 - still no sound on the P5Q-EM mobo for the ALC1200. Removing the Nvidia GTX260 doesn't help either ;-) Anyone have any possible solutions to try?

Cheers!

---

### Post by jesper1266 on 2008-11-06
Try executing:
lspci | grep -i audio

and post the result here. Maybe we can help

Cheers Jesper

---

### Post by CapoeiraFighter on 2008-11-07
I have a similar problem. No sound. Motherboard ASUS P5QL-EM.

```
lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
```

I hope that there is a solution to the problem.

---

### Post by Nominar on 2008-11-07
I also have this problem, I have a P5QL-EM motherboard and a NVIDIA 9600 graphics card.

I found a workaround in the Fedora forums : [http://fedoraforum.org/forum/showthread.php?t=203389](http://fedoraforum.org/forum/showthread.php?t=203389)

Translated into ubuntu the solution becomes:

Add the following line:
options snd-hda-intel probe_mask=1
to /etc/modprobe.d/alsa-base
It works for me!

---

### Post by CapoeiraFighter on 2008-11-07
Nominar, I love You!!! Big tnx!!! It works for me to!!!

---

### Post by jesper1266 on 2008-11-07
Thank you! 

Solution confirmed to work on my system with the standard 1.017 alsa drivers from ubuntu (installing 1.018 detects the soundcard as a ACL 1200). 

I'm up and running. Finally i can get rid of my secondary crap sondcard.

Once again tahnk you

Cheers

Jesper

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-09
> **Nominar said:**
> I also have this problem, I have a P5QL-EM motherboard and a NVIDIA 9600 graphics card.

I found a workaround in the Fedora forums : [http://fedoraforum.org/forum/showthread.php?t=203389](http://fedoraforum.org/forum/showthread.php?t=203389)

Translated into ubuntu the solution becomes:

Add the following line:
options snd-hda-intel probe_mask=1
to /etc/modprobe.d/alsa-base
It works for me!

ya i have the same sound card i tried this and it work and then stoped working it seams to just depends on magic at boot
but if it works after a boot it work until i restart then its luck of the draw

---

### Post by Is_907 on 2008-11-28
> **CapoeiraFighter said:**
> I have a similar problem. No sound. Motherboard ASUS P5QL-EM.

```
lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
```

I hope that there is a solution to the problem.

Same results from those commands here. Tried the Nominar solution with no luck, too.]

EDIT: Kubutnu 8.10... 2.6.27-9-generic (fresh install)

---

### Post by redDEADresolve on 2009-02-14
Yup that fixed my problem.


> **Nominar said:**
> I also have this problem, I have a P5QL-EM motherboard and a NVIDIA 9600 graphics card.

I found a workaround in the Fedora forums : [http://fedoraforum.org/forum/showthread.php?t=203389](http://fedoraforum.org/forum/showthread.php?t=203389)

Translated into ubuntu the solution becomes:

Add the following line:
options snd-hda-intel probe_mask=1
to /etc/modprobe.d/alsa-base
It works for me!

---

### Post by Skerit on 2009-06-03
I've got another card that's throwing a fit:

$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC1200

I've tried the workaround posted above, but it didn't work.

---

### Post by jimzhang on 2009-06-19
> **Skerit said:**
> I've got another card that's throwing a fit:

$ lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC1200

I've tried the workaround posted above, but it didn't work.

I've got the same card, and did the same thing with no luck...

---

### Post by jimzhang on 2009-06-21
> **jimzhang said:**
> I've got the same card, and did the same thing with no luck...


O, I made a stupid mistake.. I forgot to change the audio line from the audio port for my sound card to the audio port for onboard sound card, now it works!!!

---

### Post by mess-mate on 2009-07-19
> **jimzhang said:**
> O, I made a stupid mistake.. I forgot to change the audio line from the audio port for my sound card to the audio port for onboard sound card, now it works!!!
Hi, got the same problem and solved it with a 2.6.30 kernel.
What do you mean about port change ? And how did you ?
Maybe it can be helpfull .
BR

---

### Post by demortes on 2009-09-19
FYI, I did the same thing mentioned in this forum, and sound now works after a reboot....

---

### Post by UnicornsRock420 on 2010-03-04
I fresh Kubuntu install of mine has no sound.

```

Prompt:~$ lspci -v | grep -i audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
Prompt:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC1200

```
The audio with the volume cranked is extremely faint, and pulseaudio daemon isn't installed. Tried the probe_mask=1 suggested solution, rebooted, still get:
```

Prompt:~$ aplay -l
aplay: device_list:223: no soundcards found...
Prompt:~$ mpg123-alsa '/path/to/file.mp3'
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
[alsa.c:157] error: cannot open device default
[audio.c:631] error: failed to open audio device
[audio.c:179] error: Unable to find a working output module in this list: alsa
[audio.c:533] error: Failed to open audio output module
[mpg123.c:773] error: Failed to initialize output, goodbye.

```Any ideas?

---

### Post by DijitalX on 2010-10-27
I was having the same issue as everyone else.  I have a Compaq dx2400 microtower with onboard sound.  The sound was coming out of the internal pc speaker but would not come out of the line out.  I read through all of these things and tried everything thing and finally found something that worked.  My codec is RealTek ALC1200 btw

```
lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

I did a search for Ubuntu and Intel 82801i and found this site
[http://www.thinkwiki.org/wiki/Intel_82801I_HDA#Ubuntu](http://www.thinkwiki.org/wiki/Intel_82801I_HDA#Ubuntu)

Here was the solution step by step, just to make it simple:

1) Open Terminal
2) type in
 ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3) when gedit opens type the following after the last line
```
options snd-hda-intel enable_msi=1
```
4) click on save and reboot your machine.

Viola.

I hope this helps someone.

---

