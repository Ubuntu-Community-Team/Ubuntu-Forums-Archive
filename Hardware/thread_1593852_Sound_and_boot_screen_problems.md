---
title: "Sound and boot screen problems"
date: 2010-10-11
forum: Hardware
---

### Post by deokisu on 2010-10-11
Hello,

**First Problem**

I am using Lenovo G555 laptop. I have to return to my previous problem with my sound. Before upgrading to 10.10 i fixed my sound and everything was fine, until... After upgrade everything went wrong: at first my headphones didn't enable when i plugged them in and after some packages updates it (sound) stopped working at all. So i returned to basis and tried to re-install alsa-driver-linuxant_1.0.23.0_all.deb. I've got an error:

```
**An unhandlable error occured.** 
There seems to be a programming error in  aptdaemon, the software that allows you to install/remove software and  to perform other package management related tasks. 
Please report this  error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.
```So i reported it [here]("https://bugs.launchpad.net/aptdaemon/+bug/657631") without any result. Then i tried to re-install my alsa-driver, but during compilation i got this nice error:
```

In file included from /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/config.h:6,
                 from /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/adriver.h:25,
                 from /usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:2:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************

```Then i figured out that even cat /proc/asound/version command returns me an error:

```
cat: /proc/asound/version: No such file or directory
```Changing file with sudo gedit /etc/modprobe.d/alsa-base.conf didn't work.
Here is some additional info:
1) [Output]("http://www.alsa-project.org/db/?f=305d0e9649e6cbe23ab5577166ff8cf0502183b6") of wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh (And this really makes me feel stupid)
2) Output of 
```
uname -a 
aplay -l 
dpkg -l | grep "alsa" 
head -n 1 /proc/asound/card*/codec#*
``` IS

```
meloman@meloman-laptop:~$ uname -a
Linux meloman-laptop 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
meloman@meloman-laptop:~$ aplay -l
aplay: device_list:235: no soundcards found...
meloman@meloman-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.23-3ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-4                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.23+dfsg-1ubuntu4                            ALSA driver sources
ii  alsa-tools                           1.0.23-3ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                       1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                           1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.30-2                                       GStreamer plugin for ALSA
meloman@meloman-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```If you need more info please let me know.

**Second Problem**

I had this one even before update to 10.10 version, but now i want to get rid of it. I saw how normally Ubuntu should start: i mean graphically. It has nice Ubuntu logo and if any test appears there, it is small and cute. But not mine. I feel like some is changing resolution of my screen on startup and it looks awful. I can provide you with some screen shots, but later. If you are familiar with this problem and know its solution, please save me.

I want to thank to all Linux community for providing such a quick and fluent help in resolving any troubles. [COLOR=DarkOrange]***THANK YOU!!!***[/COLOR]

---

### Post by deokisu on 2010-10-12
Ok, now i  am sure that alsa-driver-linuxant caused my problems with sound. I updated kernel and everything returned to the state when my headphones didn't work when i plugged them in. Problem with installing alsa-driver-linuxant still persist, but now at least i can post output of commands as the should be.

1. [Output]("http://www.alsa-project.org/db/?f=b622cc34b5bbb9093f5b865f823db4d2ebdb6a24") of wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
2. Output of
```
uname -a  
aplay -l  
dpkg -l | grep "alsa" 
head -n 1 /proc/asound/card*/codec#*
```IS 
```

meloman@meloman-laptop:~$ uname -a 
Linux meloman-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux
meloman@meloman-laptop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
meloman@meloman-laptop:~$ dpkg -l | grep "alsa" 
ii  alsa-base                            1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-firmware-loaders                1.0.23-3ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                             1.0.17-4                                        ALSA wrapper for OSS applications
ii  alsa-source                          1.0.23+dfsg-1ubuntu4                            ALSA driver sources
ii  alsa-tools                           1.0.23-3ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                       1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                           1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                           4.69-0ubuntu2                                   Bluetooth audio support
ii  gnome-alsamixer                      0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                   0.10.30-2                                       GStreamer plugin for ALSA
meloman@meloman-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20585
```So now the point is to make my headphones work as they should. 

P.S. Problem with re-installing alsa-driver with script still persist.

---

### Post by deokisu on 2010-10-14
Issue with headphones was solved, when i changed model to thinkpad, but microphone doesn't work after this action.

---

### Post by daniellehudges on 2010-10-14
In my case, I did change headset more than twice and my only problem is my mic doesn't work and I don't understand the reason. I did update my sound manager and checked the settings but till now it's still the same. Anyone could help us solve this problem?

---

### Post by deokisu on 2010-10-18
One guy helped me a lot, but not till fully solving the problem. That is what i got:
> 
seem using Node 0x14 according to hda-emu

but node 0x23 seem not Mic on your computer

you can use hda_analyzer to test/change the amp values/mute switch and connection of those nodes in the audio path?

the blue lines in the graph are connected

[Audio Input] ---> ....[Audio selector/Mixer] ----> [Pin complex] Mic

But that is the place, where I am really lost. I got that far and stuck. Please help me to finally solve it. Here are screenshots. 

[http://img69.imageshack.us/i/screenshotmfi.png](http://img69.imageshack.us/i/screenshotmfi.png)
[http://img841.imageshack.us/img841/4052/screenshot1yr.png](http://img841.imageshack.us/img841/4052/screenshot1yr.png)

Here is [link]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5157") to the original post.

---

### Post by deokisu on 2010-10-19
Please help me to finish it or tell where am i wrong?

---

