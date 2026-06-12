---
title: "No Audio in Ubuntu 10.4 on Vaio Laptop"
date: 2010-06-08
forum: Hardware
---

### Post by smiccoli on 2010-06-08
Hello to all! 

I've searched in a lot of threads and all solutions didn't apply to my situation.

Last week I was hearing music with no problem, and yesterday I got no sound at all...

My laptop is a **Vaio** VPC-EB14FD with HDA Intel **Realtek ALC269**. 

Now some outputs of my system:

**uname -a**
```
Linux sandro-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```**aplay -l**
```
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC269 Analog [ALC269 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: Generic [HD-Audio Generic], dispositivo 3: ATI HDMI [ATI HDMI]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0

```**cat /proc/asound/version**
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  7 2010 for kernel 2.6.32-22-generic (SMP).

```**head -n 1 /proc/asound/card*/codec#***
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```Oh, and the system was upgraded from 9.10 version.

Thanks!

---

### Post by Yellow Pasque on 2010-06-09
> Advanced Linux Sound Architecture Driver Version 1.0.23.
If you used the ALSA upgrade script, you need to re-run it with the -c and -i options after each kernel update.

---

### Post by lidex on 2010-06-09
Did you lose sound just after the upgrade to lucid?
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by rablanken on 2010-06-09
I had the same problem for a long time (VAIO laptop, native speakers refuse to play). This fixed it, might work for you too.

Try installing "pulseaudio volume control", and running that program.  It should be able to be installed by searching "pulseaudio volume control" into Applications>Ubuntu Software Center and clicking "install".

---

### Post by smiccoli on 2010-06-09
> **lidex said:**
> Did you lose sound just after the upgrade to lucid?
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```Logout/in.

Lidex, thank you **so** much!!
This solved my problem!!

---

### Post by smiccoli on 2010-06-09
This is weird...

I get sound from the system, from firefox, but from softwares like **exaile**, **vlc**, **totem**, I get nothing...

Any clues?

---

### Post by smiccoli on 2010-06-09
The way I solved that problem was changing the audio output to Analog Stereo and not Manhattan HDMI Audio Digital Stereo!

---

### Post by smiccoli on 2010-06-09
Sorry for posting a lot, but this problem is very strange...

Now look what happens: if I reboot and play Exaile it works great, but if I try to play some music in Firefox, nothing happens and then when I go back to Exaile it doesn't work either...

Any suggestions?

---

### Post by lidex on 2010-06-09
Try this.
[http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

---

### Post by birurajak on 2010-06-22
Hello to all..
I have Vaio VPCEB14EN, installed ubantu 10.4, but i dont get any sound at all, not even staring sound. I have already window 7 basic. Pls help me.

---

### Post by mlichtenstein2 on 2010-09-11
I upgraded from Ubuntu 8.04 to 10.04 and now I do not have
sound in Firefox ([www.youtube.com](www.youtube.com)). However, I do have sound when playing wmv and mp3 files.
I already ran: sudo apt-get install flashplugin-nonfree-extrasound
and rebooted my Sony Vaio PCG-7V2L

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

uname -a
Linux mark-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

Placing the following in /etc/asound.conf did not work for me.
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

I do have a work around and that is to use the Epiphany Browser instead of Firefox.

Any ideas,

Mark Lichtenstein
[email]mlichtenstein2@earthlink.net[/email]

---

### Post by Yellow Pasque on 2010-09-11
flashplugin-extrasound is for those using OSS4 (instead of ALSA/pulse), so I don't think you want it installed.
Did you try this?: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by lidex on 2010-09-14
> **Temüjin said:**
> flashplugin-extrasound is for those using OSS4 (instead of ALSA/pulse), so I don't think you want it installed.
Did you try this?: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

Self-promoter!
Kidding. Just back from vacation. Good to see you Crazy Horse.;)

---

### Post by mlichtenstein2 on 2010-09-14
Placing the following in /etc/asound.conf did not help.
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

However, a good work around is to use the Epiphany Browser.

Mark Lichtenstein

---

### Post by Yellow Pasque on 2010-09-14
> **lidex said:**
> Self-promoter!
I often promote myself, but not nearly as much as I degrade myself. Nice to see you back as well, uber-helpful info-gathering man. ):P

---

