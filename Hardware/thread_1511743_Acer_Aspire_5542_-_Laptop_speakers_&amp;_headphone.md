---
title: "Acer Aspire 5542 - Laptop speakers &amp; headphones playing at the same time"
date: 2010-06-17
forum: Hardware
---

### Post by Godspell on 2010-06-17
Hello all,

I know these are old problems and I've read through some of the solutions out there but I can't seem to find anything good for me.

Following is my user environment.

Ubuntu 10.04 64-bit
Acer Aspire 5542
AMD Turion 2 X2 M500 (2.2 GHz, 1MB L2 Cache)
ATI Radeon HD4200
4GB DDR2 RAM

_Audio Device_ Intel HDA SBx00 Azalia
ALSA Driver 1.0.23

This happens everytime I try to switch between laptop speakers and headphones.
If I want to switch to headphones, I have to plug it in and reboot the laptop.
It's not entirely persistent though. When I'm very (very) lucky sometimes, it just works.

I tried to solve it by setting the laptop speaker volume off from Alsamixer (in terminal) while the head phones are plugged in, but it doesn't work because I can still fadely hear the sound from laptop speakers.

I've come across an old thread on adding a switch to "Sound Preferences" and I don't like the idea (no disrespect to the original uploader), because I think the sound should work intelligently just like it did on Windows.

There must be a solution to his problem. I love Ubuntu and I never think of going back to Windows, but this is really getting on my nerve.
I can't listen to anything while I'm doing some works in the library!

On top of this problem, **the mic won't work!**
Again, it worked flawlessly back in Windows.
I want to use the mic attached to headphone to use Skype or Empathy.
I've made sure it's not muted from the Alsamixer (yes, it does detect) but it still won't work.

So, please (please) help me find the solutions for both of these problems.
I desperately want to sort them out.

Thank you very much.

Regards,
GS

---

### Post by lidex on 2010-06-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

> I've come across an old thread on adding a switch to "Sound Preferences" and I don't like the idea (no disrespect to the original uploader), because I think the sound should work intelligently just like it did on Windows.

If the manufacturer would provide a driver for linux specific to your soundchip, as it does for windows, this would be the case. Unfortunately alsa has to handle every configuration with little or no documentation from manufacturers and "adding a switch" becomes necessary.

---

### Post by Godspell on 2010-06-17
Can you post the output of these terminal commands for me please:

uname -a
```
Linux laptopname 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC  2010 x86_64 GNU/Linux
```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```dpkg -l | grep "alsa"
```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
```head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
```**Please also include the make/model of your PC/Laptop.**

I did mention this in the first place.
```
Ubuntu 10.04 64-bit
Acer Aspire 5542
AMD Turion 2 X2 M500 (2.2 GHz, 1MB L2 Cache)
ATI Radeon HD4200
4GB DDR2 RAM
```> If the manufacturer would provide a driver for linux specific to your soundchip, as it does for windows, this would be the case.
Unfortunately alsa has to handle every configuration with little or no documentation from manufacturers and "adding a switch" becomes necessary.To be honest, I've not tried that option before. I've read through it and even got stuck at one point.
But haven't completely tried it.

Let me know if you have any other way around for this.
If not, adding a switch is a last resort.

Thank you and regards,
GS

---

### Post by lidex on 2010-06-17
Well, you can try the alsa-upgrade-script - there's a link in my sig. That may do the trick in itself, although it's a little more complicated. Adding the switch would involve this:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by Godspell on 2010-06-17
My ALSA is already 1.0.23. I upgraded myself last week.

I guess I'll have to add the switch, in this case.

Thanks for your reply.

Regards,
GS

---

### Post by lidex on 2010-06-17
> **Godspell said:**
> My ALSA is already 1.0.23. I upgraded myself last week.



According to dpkg you're not. 
```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities

```

---

### Post by Godspell on 2010-06-17
Right, ok. I'll try following the instructions on your link and do it so, again.

When I did "cat /proc/asound/version" it says
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 11 2010 for kernel 2.6.32-22-generic (SMP)
```I wonder why it didn't work. Anyway, thanks for pointing that out.
I hope this will also solve the mic problem.

Regards,
GS

---

### Post by Godspell on 2010-06-19
> According to dpkg you're not.Dude, I've just upgraded the ALSA drivers again but this time, using your script.
Everything went well and I can hear my sound well.
I feel like nothing has changed so I did [U]cat /proc/asound/version
[/U]```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 20 2010 for kernel 2.6.32-22-generic (SMP).
```It doesn't change anything apart from the compiled date. 
I also did _dpkg -l | grep "alsa"_
```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                 1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                              1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                           1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                            1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                        1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA

```Again, the same result, saying 1.0.22. Maybe it's meant to use this version in some cases???
And the sound is still playing from both laptop speakers and headphones at the same time. So, I think I'll just add the bloody switch :|

Anyway, just letting you know. If you've got any thoughts on this, give me a shout.

Cheers and regards,
GS

---

### Post by lidex on 2010-06-19
Ah, OK...
> The script is not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files.
You won't see any changes on the ALSA package-ids within Synaptic!
You've got 1.0.23. Aplay reports correctly. If you had alsa-backports installed then it wouldn't update. You just need more. My laptop is the same way.

---

### Post by Godspell on 2010-06-20
Right, I've got a new problem.
As mentioned earlier, the drivers upgrade was fine and no problem occured.
But adding the switch doesn't work at all and in fact, it locked the access to "Headphone" in Alsamixer (terminal). So, I pulled it off.
I really don't know what to do with this problem.

Since you seem to know a lot of audio, I've got a question for you.
It's related to volume control. You know how you can control the volume from laptop, yeah? it's got + - buttons above they keyboard.
When I max out the volume from there, the actual volume from "Sound Preferences" doesn't get maxed out.
It got stuck at like 80%. I attached a screenshot for that.

Would it be possible for me to max out the volume without going to "South Preferences"?
Let me know.

Thank you very much.

Regards,
GS

---

### Post by necrologist on 2010-07-02
Hi,

I'm on 5542 too, I had this (thread name) problem only a few times in three months, but I've got a way more annoying (at least for me);
Pulseaudio sink (mic) gets suspended every now and then (I have no sure way to reproduce this), I found out that this may be caused by some application grabbing the alsa input.

You can use this script to restart Pulseaudio and Alsa, to get your sound back without rebooting, but you will need to restart every application too which you want to hear.
(You have to give it your sudo password as the first argument)
```
#!/bin/bash
echo autospawn = no >> ~/.pulse/client.conf
echo $1 | sudo -S killall pulseaudio
echo $1 | sudo -S alsa force-reload
pulseaudio -D
rm ~/.pulse/client.conf
```

The other thing which may help us is finding out the most compatible model for snd-hda-intel module; this could be done by adding
```
options snd-hda-intel model=XXXXX
```
to the end of
/etc/modprobe.d/alsa-base.conf

where XXXXX should be substituted by a model from
/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
HD-Audio-Models.txt line ~ 117 (ALC888 section)

I had nor time nor nerve to try out the different options yet, but if someone has them please feel free to post any result ;)

edit #1 partial results:
**spk/head autoswitch	mic bug	spk/head bug	speaker	headphone	mic (external)	model	Description**
-	n/a	n/a	x	-	x	3stack-dig	3-jack with SPDIF I/O
-	n/a	n/a	x	-	x	6stack-dig	6-jack digital with SPDIF I/O
-	n/a	x	x	x	x	3stack-6ch	3-jack 6-channel
-	n/a	x	x	x	x	3stack-6ch-dig	3-jack 6-channel with SPDIF I/O
-	n/a	x	x	x	x	acer	Acer laptops (Travelmate 3012WTMi, Aspire 5600 etc)
-	n/a	n/a	-	-	x	acer-aspire	Acer Aspire 9810
[B]x	n/a	-	x	x	x	acer-aspire-4930g	Acer Aspire 4930G
x	n/a	-	x	x	x	acer-aspire-6530g	Acer Aspire 6530G
x	n/a	-	x	x	x	acer-aspire-7730g	Acer Aspire 7730G[/B]
-	n/a	n/a	-	-	-	acer-aspire-8930g	Acer Aspire 8930G

---

### Post by ferubu on 2010-07-02
Hi, I'm Fernando and I have the same problem with the mic and sound.

The mic doesn't work with these solutions, when I conect my headphones the speakers sounds. The mic doesn't work. I don't know what happen, I need the mic because I use Skype. 


Please help me.

I'm a new in Ubuntu. I installed Ubuntu 10.4

My laptop is Acer Aspire 5542 - 1241

Thanks

---

### Post by Godspell on 2010-07-14
> **necrologist said:**
> Hi,

I'm on 5542 too, I had this (thread name) problem only a few times in three months, but I've got a way more annoying (at least for me);
Pulse audio sink (mic) gets suspended every now and then (I have no sure way to reproduce this), I found out that this may be caused by some application grabbing the alsa input.


Mate, thanks for making an effort to post something useful like this in my thread.
However, I'm afraid your knowledge in Ubuntu (sound) is way more advanced than mine.
I thought Pulse Audio was only in previous versions of Ubuntu like Fiesty?
Now we've been a long way from then on and I'm using Lucid 64bit, ALSA drivers 1.0.23.
So, do we still have Pulse audio in our machines?

Man, the mic is a BIG problem on Acer 5542. It's bloody annoying that I feel like smashing my laptop sometimes. In the past, it had worked with Skype for like a day but afterwards, it just dropped.

The same for the "thread name" problems. They never go away completely.

Anyway, you guys let me know if there are simple ways to this problems.
So far, VOIP was hardly ever possible in Ubuntu.

Regards,
GS

---

### Post by cpbl on 2010-07-15
I have a related problem. My laptop has been working fine for YEARS and for MONTHS under the current operating system. Then, suddenly, not just after a boot, the main speakers turned on when I was listening through headphones and now I cannot listen through the headphones without it playing out loud!!

That is bizarre. Is anyone able to give me a hand??

(If this is a different problem, I can start a new thread, since my hardware is not Acer Aspire. It's an Asus S62E)

```
[1822][cpbl@:~]$ uname -a
Linux cpbl-server 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
[1823][cpbl@:~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[1823][cpbl@:~]$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
[1823][cpbl@:~]$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Generic 1543 Si3054
```


Thanks,
c

---

### Post by Godspell on 2010-07-17
You can use my thread, it's no problem. Although, I don't think not many people here know how to solve these problems, let alone provide us the correct solution.

I really wish the forum administrators, moderators or other Ubuntu official developers would look into this audio complexity and actually troubleshoot!
But hey, a wish is just a wish, innit?

The same thing happened on my laptop, the mic did work but it was NOT persistent.
It's frustrating because everything on my laptop work well with Ubuntu apart from mic.
You see I was never able to listen to music with my headphones (whilst I'm in the library doing my work) or speak to my family through Empathy.

Anyway, enough with my negativity...or eventually, I'll get really wound up just thinking about this.

Hope, there'll be a day where we can all FULLY enjoy the experience of "mobile" Ubuntu.
(There's nothing wrong with the laptop because everything was working well on Windows 7.)

Until then...

Best regards,
GS

---

### Post by lidex on 2010-07-17
> **cpbl said:**
> I have a related problem. My laptop has been working fine for YEARS and for MONTHS under the current operating system. Then, suddenly, not just after a boot, the main speakers turned on when I was listening through headphones and now I cannot listen through the headphones without it playing out loud!!

That is bizarre. Is anyone able to give me a hand??

(If this is a different problem, I can start a new thread, since my hardware is not Acer Aspire. It's an Asus S62E)

```
[1822][cpbl@:~]$ uname -a
Linux cpbl-server 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
[1823][cpbl@:~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[1823][cpbl@:~]$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
[1823][cpbl@:~]$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Generic 1543 Si3054
```


Thanks,
c

With your's there's a chance that an update reset your configuration. Look in your 'Sound Preferences' - the profile on the 'Hardware' tab and the 'Connector' on the 'Output' tab. Had you upgraded alsa at some point previously and then installed a new kernel the upgrade would need to be re-applied as well. You may want to check with gnome-alsamixer to make sure 'jack-sense' is enabled also. Some times you need to toggle the settings to get them working again.

---

### Post by lidex on 2010-07-17
> **Godspell said:**
> You can use my thread, it's no problem. Although, I don't think not many people here know how to solve these problems, let alone provide us the correct solution.

I really wish the forum administrators, moderators or other Ubuntu official developers would look into this audio complexity and actually troubleshoot!
But hey, a wish is just a wish, innit?

The same thing happened on my laptop, the mic did work but it was NOT persistent.
It's frustrating because everything on my laptop work well with Ubuntu apart from mic.
You see I was never able to listen to music with my headphones (whilst I'm in the library doing my work) or speak to my family through Empathy.

Anyway, enough with my negativity...or eventually, I'll get really wound up just thinking about this.

Hope, there'll be a day where we can all FULLY enjoy the experience of "mobile" Ubuntu.
(There's nothing wrong with the laptop because everything was working well on Windows 7.)

Until then...

Best regards,
GS
I guess we all need to vent sometimes but it's difficult for the limited amount of people and resources to fix everything immediately when you have so much new hardware coming out all the time. For the most part, the manufacturers are not helping because, guess what, there's no money in it for them. Probably the greatest aspect of ubuntu is the community and as a community, we all benefit when individuals take it upon themselves to provide solutions - even as simple as reporting a bug so the devs can fix it.

---

### Post by bizon on 2010-10-07
Hi guys!
I have problem with sound on my aspire 5542G.
I don't have /proc/asound directory.
The problem appeared aftep upgrade to Maverick Meerkat.
Please upload files(or show) from /proc/asound for me.

---

### Post by lidex on 2010-10-07
> **bizon said:**
> Hi guys!
I have problem with sound on my aspire 5542G.
I don't have /proc/asound directory.
The problem appeared aftep upgrade to Maverick Meerkat.
Please upload files(or show) from /proc/asound for me.
Yeah I don't think it works that way. You should try re-installing alsa. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by bizon on 2010-10-08
Don't work.

uname -a
```
Linux pasha-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

```

aplay -l
```
aplay: device_list:235: no soundcards found...
```

dpkg -l | grep "alsa"
```
ii  alsa-base                                      1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.23-3ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-4                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.23+dfsg-1ubuntu4                            ALSA driver sources
ii  alsa-tools                                     1.0.23-3ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                 1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                                0.99.80-5build1                                 PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                              0.99.80-5build1                                 PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                 0.99.80-5build1                                 PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-jack                                0.99.80-5build1                                 PCM player designed for ALSA (JACK output module)
ii  alsaplayer-oss                                 0.99.80-5build1                                 PCM player designed for ALSA (OSS output module)
ii  bluez-alsa                                     4.69-0ubuntu2                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.30-2                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                14.3.1-1build1                                  SoX alsa format I/O library
ii  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-backports-modules-alsa-2.6.32-25-generic 2.6.32-25.23                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-backports-modules-alsa-2.6.35-22-generic 2.6.35-22.12                                    Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.21.22                                    Backported drivers for alsa-driver snapshot.
ii  linux-backports-modules-alsa-maverick-generic  2.6.35.22.23                                    Backported drivers for alsa-driver snapshot.
ii  xmms2-plugin-alsa                              0.7DrNo+dfsg-2                                  XMMS2 - ALSA output

```

head -n 1 /proc/asound/card*/codec#*
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

Thanks.

---

### Post by bizon on 2010-10-08
Don't work.

uname -a
```
Linux pasha-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

```

aplay -l
```
aplay: device_list:235: no soundcards found...
```

dpkg -l | grep "alsa"
```
ii  alsa-base                                      1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.23-3ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-4                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.23+dfsg-1ubuntu4                            ALSA driver sources
ii  alsa-tools                                     1.0.23-3ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                 1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                                0.99.80-5build1                                 PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                              0.99.80-5build1                                 PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                                 0.99.80-5build1                                 PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-jack                                0.99.80-5build1                                 PCM player designed for ALSA (JACK output module)
ii  alsaplayer-oss                                 0.99.80-5build1                                 PCM player designed for ALSA (OSS output module)
ii  bluez-alsa                                     4.69-0ubuntu2                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.30-2                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                14.3.1-1build1                                  SoX alsa format I/O library
ii  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-backports-modules-alsa-2.6.32-25-generic 2.6.32-25.23                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-backports-modules-alsa-2.6.35-22-generic 2.6.35-22.12                                    Ubuntu supplied Linux modules for version 2.6.35 ALSA snapshots.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.21.22                                    Backported drivers for alsa-driver snapshot.
ii  linux-backports-modules-alsa-maverick-generic  2.6.35.22.23                                    Backported drivers for alsa-driver snapshot.
ii  xmms2-plugin-alsa                              0.7DrNo+dfsg-2                                  XMMS2 - ALSA output

```

head -n 1 /proc/asound/card*/codec#*
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

lspci | grep Audio
```
0:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

Thanks.

---

### Post by lidex on 2010-10-08
Use synaptic to remove all the alsa-backport packages you have installed. Next remove your old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
(You can ignore any 'not found' errors)
Now re-install alsa again:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by bizon on 2010-10-09
I did your recomendation, but it don't work. After rebooting disappeared sound icon in tray.

head -n 1 /proc/asound/card*/codec#*
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

aplay -l
```
aplay: device_list:235: no soundcards found...
```

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[http://www.alsa-project.org/db/?f=bed2214468680a9e40e638348755a801477b6eda](http://www.alsa-project.org/db/?f=bed2214468680a9e40e638348755a801477b6eda)

Thanks that helping me.

---

### Post by lidex on 2010-10-10
> **bizon said:**
> I did your recomendation, but it don't work. After rebooting disappeared sound icon in tray.

head -n 1 /proc/asound/card*/codec#*
```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

aplay -l
```
aplay: device_list:235: no soundcards found...
```

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
[http://www.alsa-project.org/db/?f=bed2214468680a9e40e638348755a801477b6eda](http://www.alsa-project.org/db/?f=bed2214468680a9e40e638348755a801477b6eda)

Thanks that helping me.

Something is probably wrong with your software sources (repositories). There may be more of a problem than that. May be easiest just to backup your home directory, format, and do a clean install.

---

