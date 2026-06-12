---
title: "Acer 5920g audio over HDMI"
date: 2009-03-20
forum: Hardware
---

### Post by theBuh on 2009-03-20
Hi all. 
I have Acer Asprire 5920g laptop running Intrepid.
I trying to get audio over HDMI working. But im failed to do so. 
Im upgraded ALSA to latest version (1.0.19).
Even installed Realtek Linux Audiopack 5.11 (wich is almost same Alsa 1.0.19)

Heres output of lspci:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Its detected by Alsa (aplay -l) as
```

card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I have sound over S/Pdif Toslink connector, buildin speakers, AC3 passtrough and everything.
But not HDMI audio. 
I think there should be device in list of aplay -L something like 
```

hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output

```
But theres none. 

In Jaunty Alpha 5 (even with pulseaudio 0.9.15 pre release) situation is the same. 

Nvidia drivers version is 180.22.

Its not hardware problem since in Windows HDMI audio working perfectly.

Any ideas?

---

### Post by theBuh on 2009-03-22
bump?

---

### Post by smith912 on 2009-03-27
I have the same problem. Alsa and Nvidia driveres are the same. 

Anybody a idea?

aplay -l:
```
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

```
aplay -L:
```
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by el_carpone on 2009-04-15
Hi,

after several hours i finally managed to get my hdmi sound working with my acer 5920g.

my problem and perhaps yours too was that i didn't upgrade alsa-utils to 1.9 which made it finally working. 

Here are the steps that brought my tv screaming:
- update alsa-base to 1.9
- update alsa-utils to 1.9
- stop your XServer, run "alsaconf", reboot 

I'm not sure if alsa-base 1.9 works, due i'm using an snapshot from 12. April but certainly worth a try.

some system info:
```

aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
 Untergeordnete Geräte: 0/1
 Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
 Untergeordnete Geräte: 1/1
 Untergeordnetes Gerät '0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.19.46.g516fa.506.gb750c.
Compiled on Apr 13 2009 for kernel 2.6.29.1 (SMP). 
```

Hopefully this helps for getting your tv receiving the sound signal :guitar:

greetings,

---

### Post by theBuh on 2009-04-15
el_capone, could you please post output of "aplay -L" too?.

---

### Post by el_carpone on 2009-04-15
sure here you go

```
aplay -L
default:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

---

### Post by theBuh on 2009-04-15
Hm could it be yours .29 kernel that makes the difference?
Since i installed latest snapshot of alsa driver and utils 
```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.19.46.g516fa.506.gb750c.
Compiled on Apr 16 2009 for kernel 2.6.28-11-generic (SMP).

```

And still no sound over hdmi =\

---

### Post by theBuh on 2009-04-16
Well i upgraded my kernel to 2.6.29.1 and recompiled alsa driver and utils, and theres still silence.

But! I saw a first glimpse of light at the end of the tunnel. 
When i tried hda-analyze tool from alsa (after a little patching) i got some results - my sound card codec audio out for hdmi (in my case node 0x10) wasnt enabled. 
After i enabled it - i finnaly got pcm stereo signal icon on my reciver.
But still cant play any sound. speaker-test -Dplug:iec985 -c6 -twav doesnt work etc.

I think i got really close to solution :) But not there yet.

Any ideas about how to route iec985 sound signal to that audio out node (0x10). I suppose atm my default node is 0x06 - which is front toslink connector.

---

### Post by ahbart on 2009-04-16
Hi
Did you enable digital audio? 
Open gnome volume applet - settings/preferences button - and select the suspected devices. When done, I get a new tab in the volume manager with switches. Including IEC958 in my case.
Could that be the case here too?

---

### Post by theBuh on 2009-04-16
Yeah ofc. Both IEC985 and IE985 Default pcm. Tho i dont know whats latter doing. It seems not affecting anything. 
And anyway toslink connector working ok.

---

### Post by el_carpone on 2009-04-16
the thing that did it for me was:

**alsaconf**

it didn't worked before i ran it, and don't forget too upgrade alsa-utils too.

The kernel upgrade is not needed in my opinion due it ships alsa 1.8a and if you compile alsa yourself the kernel stuff is overwritten.

Another thing, i'm using nvidia driver 180.44


greetings,

---

### Post by theBuh on 2009-04-16
Yaaaay i finnaly managed to get hdmi audio working!

In my desperate attempts i downloaded and compiled 
alsa-lib-1.0.19.18.ga987a
alsa-utils-1.0.19.10.g658ce
alsa-plugins-1.0.19.12.g23263

```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.19.46.g516fa.506.gb750c.
Compiled on Apr 16 2009 for kernel 2.6.29-02062901-generic (SMP).

```

Tried alsaconf several times. 
But i think thing that finnaly made the trick was 
line in /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=auto

(at least this was last thing that i did before reloading alsa with success :D )

---

### Post by Blackkitten on 2009-05-11
Hello!
alsaconf didn't help me. 
I've got the same symtomps.

Can anyone post a tutorial or smth like that with all main steps?

---

### Post by theBuh on 2009-05-11
Your alsa and alsa-utils version?

---

### Post by Blackkitten on 2009-05-11
I've updated till 1.20 using this post [http://ubuntuforums.org/showthread.php?t=1151344&highlight=alsa]("http://ubuntuforums.org/showthread.php?t=1151344&highlight=alsa")
> 
sam@sam-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on May 11 2009 for kernel 2.6.28-11-generic (SMP).


aplay -l:
> **** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC1200 Analog [ALC1200 Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC1200 Digital [ALC1200 Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
sam@sam-laptop:~$ 


aplay -L:
> default:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


I'm using 185.19 nvidia drivers.

---

### Post by Blackkitten on 2009-05-12
bump

---

### Post by theBuh on 2009-05-13
Do you have any additional options in /etc/modprobe.d/alsa-base.conf for 
 snd-hda-intel?

I've updated Alsa to 1.0.20 but not tested hdmi audio with it yet.

upd: Yep it works :)

---

### Post by theBuh on 2009-05-13
Well all the steps i can suggest is:
1) Update alsa driver and alsa utils (if its not latest.)  Heres a handy script for that (if you lazy to do it manually): [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
2) Run alsaconf
2a) Reboot or restart alsa.
3) Check Volume control for IEC958c checkbox (should be on)

And HDMI audio doesnt work if secondary display disabled in nvidia-settings btw (just figured it out :) ).

---

### Post by Blackkitten on 2009-05-14
> # autoloader aliases
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

it's my /etc/modprobe.d/alsa-base.conf

HDMI audio still doesn't work.
What do you choose under System>Sound to play HDMI audio?

---

### Post by theBuh on 2009-05-14
Hm i have it on auto. 
Ok try to add 
```

options snd-hda-intel model=auto

```
to the end of  /etc/modprobe.d/alsa-base.conf.  Well it should be default setting but in my case it somehow wasn't. Then reload alsa or reboot. Make sure your IEC958 checkbox is on in Volume Control.
Also make sure you enable your second monitor in nvidia settings. then you should be ok. You can try speaker test:
```

$ speaker-test -Dplug:iec958 -c2 -twav

```

If it doesn't work you can check your /proc/asound/card0/codec#0 and look for these lines (HDMI audio output and HDMI connector) if its enabled at all.

```

Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: **Enabled** GenLevel
  Digital category: 0x2
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x1856e130: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = White
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10


```

If its not. You can try to download HDA Analyzer tool from here [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

Theres bug in code tho. You need to patch hda_codec.py around line 730 and add 
```

  def rw(self, nid, verb, param):
    """do elementary read/write operation"""
    [b]if not nid:
      nid = 0[/b]

```

And then try to enable HDMI output from there.

---

### Post by Blackkitten on 2009-05-17
I don't have vy notebook with me. So I can not try your ideas.
But in the end of the week I'll try and will write about results!

---

### Post by Blackkitten on 2009-05-22
Ok, addind code you wrote helped me!
Thanks a lot!
But Know I can't output 1080p video. I get 1080i instead:-(

---

### Post by Blackkitten on 2010-06-24
So, it's year 2010. I'm using Ubuntu 10.04. But the problem is the same:-(.

And so is the solution:
"add a line in /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=auto"

---

