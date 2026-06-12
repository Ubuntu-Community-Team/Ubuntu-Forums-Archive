---
title: "hda Intel soundcard solution"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by eggdeng on 2006-12-07
This solution may work for you if alsa is properly configured, ie sound seems to be working in every respect except that you simply can't hear it or, for example, can hear it on headphones but not on integrated speakers. 

Many posters have pointed out that the solution to the problem is often as simple as adding a line at the end of /etc/modprobe.d/alsa-base along the lines of

```
options snd-hda-intel model=xyz
```

The problem here is that xyz is different for different makes of laptop. For HP laptops, you (usually) need to put 'hp' (no quotes), my LG laptop requires 'lg' (no quotes), other options I have seen are 'asus', 'w180', 'uniwill' (again, no quotes).

On dapper, you can find one list of possible options in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz. Gunzip it, open with gedit and search for your soundcard chip. To check which chip you have ```
aplay -l
```Sample entry from ALSA-Configuration.txt:

ALC260
	  hp		HP machines
	  fujitsu	Fujitsu S7020

This tells you that if you have an ALC260 chip on a HP laptop, the appropriate value is 'hp'. And so on and so forth.


UPDATE

The following are some of the known good options for this fix and links to  threads & posts in which they are confirmed to work.

Acer ???
```
options snd-hda-intel model=ACER
```
[http://ubuntuforums.org/showthread.php?t=202555&page=5&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=202555&page=5&highlight=Intel+HDA)
#41

Asus F3J
```
options snd-hda-intel model=uniwill-m31
```
[http://ubuntuforums.org/showthread.php?t=310717&highlight=Intel+HDA??](http://ubuntuforums.org/showthread.php?t=310717&highlight=Intel+HDA??)
post unknown

Dell 6400 laptop
```
options snd-hda-intel model=dell
```
[http://ubuntuforums.org/showthread.php?t=302543&page=2&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=302543&page=2&highlight=snd_hda_intel) #14

Dell Inspiron
```
options snd-hda-intel model=ref
```
[http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200)
post unknown

Dell Dimension 9150
```
options snd-hda-intel model=ref
```
[http://ubuntuforums.org/showthread.php?t=251877&page=2&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=251877&page=2&highlight=Intel+HDA) 
post unknown

Fujitsu Siemens Amilo XI 1526
```
options snd-hda-intel model=fujitsu
```
[http://ubuntuforums.org/showthread.php?t=465422&page=2](http://ubuntuforums.org/showthread.php?t=465422&page=2)

Gateway laptops with a sigmatel audio device  
```
options snd-hda-intel probe_mask=1
```
[http://ubuntuforums.org/showthread.php?t=348517&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=348517&highlight=Intel+HDA) #2
or
```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```
thread unknown, post unknown

Lenovo	???
```
options snd-hda-intel model=laptop-eapd
```
[http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel) #2

LG P1 Express Dual (ALC880 chip)
```
options snd-hda-intel model=lg
```
[http://ubuntuforums.org/showthread.php?t=347088&highlight=Intel+HDA](http://ubuntuforums.org/showthread.php?t=347088&highlight=Intel+HDA)
post unknown

LG P1 with CMI9880 chip
options snd-hda-intel model=minimal
[http://ubuntuforums.org/showthread.php?t=465422&page=2](http://ubuntuforums.org/showthread.php?t=465422&page=2)

Toshiba Satellite a135-s2386
```
options snd-hda-intel probe_mask=8 model=3stack
```
[http://ubuntuforums.org/showthread.php?t=452992](http://ubuntuforums.org/showthread.php?t=452992)


Toshiba Tecra A8-103
```
options snd-hda-intel probe_mask=8 model=fujitsu
```
Thread unknown
or
```
options snd-hda-intel probe_mask=8 model=fujitsu
```
See this thread, post #42

More help is available from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). The following is quoted (with a small edit) from that source:

options snd-hda-intel model=3stack works for many motherboard integrated chips with shared surrounds. Other models include 5stack, 6stack, laptop and laptop-eapd. Sometimes it is also possible to use the more generic "options snd-hda-intel model=ref", which the hda driver uses to load manufacturer specfic presets (SigmaTel, Realtek, etc.). The full list is available in ALSA-Configuration.txt in the driver tarball under alsa-kernel/Documentation/.



UPDATE

A guy in this thread has found a solution to the microphone problem.
[http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)

---

### Post by MadeR on 2007-01-01
[http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260](http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260)

---

### Post by MWP on 2007-01-01
eggdeng...

You say youve got a LG LWxx.
Have you got audio out on the inbuilt speakers working?
I can only get audio out of the headphone jack.
](*,)

---

### Post by eggdeng on 2007-01-01
It's an LG P1 Express Dual & a beautiful piece of work. I did have the same problem as you to begin with, so don't give up, you'll be able to get it to work. It's a while since I set it up so I can't remember all the steps but you will need at least alsa 1.0.13. If I were you, I would follow MadeR's how-to to set up alsa and just change the last step as indicated in the original post. Good luck.

---

### Post by MWP on 2007-01-02
But... how did you move sound to the speaker outputs instead of line/headphone out?

Ive updated to alsa 1.0.13 from the Fiesty repositories (im running Edgy), am still using "lg-lw" as the hda type option.
Sound still only comes from the line-out.

None of the switches in alsamixer help.

Any ideas?

---

### Post by eggdeng on 2007-01-02
What solved the problem for me was simply inserting```

options snd-hda-intel model= lg
``` in /etc/modprobe.d/alsa-base. From your post, you seem to be using 'lg-lw' where I am using 'lg'. Try with just 'lg'.

---

### Post by MadeR on 2007-01-02
> **eggdeng said:**
> What solved the problem for me was simply inserting```

options snd-hda-intel model= lg
``` in /etc/modprobe.d/alsa-base. From your post, you seem to be using 'lg-lw' where I am using 'lg'. Try with just 'lg'.

option "lg" is not among the recognized ones, i think the module automatically uses "auto"

---

### Post by Zoandar on 2007-03-27
I can't edit the alsa-base file, because it says I don't have permission. I installed this OS, and there has been no other person near this notebook. How do I tell it I am an administrator, so I can try your suggestion? ( HP DV1000).

Larry

---

### Post by MadeR on 2007-03-28
> **Zoandar said:**
> I can't edit the alsa-base file, because it says I don't have permission. I installed this OS, and there has been no other person near this notebook. How do I tell it I am an administrator, so I can try your suggestion? ( HP DV1000).

Larry

use the sudo command

for example ```

sudo vim /etc/alsa

```

if you are using kde and you need a window application (for example "kate") use kdesu instead.
there is a similar command for gnome, if I am not wrong gtksudo or gsudo, but I do not remember the name.

---

### Post by julian67 on 2007-03-30
> **eggdeng said:**
> This solution may work for you if alsa is properly configured, ie sound seems to be working in every respect except that you simply can't hear it or, for example, can hear it on headphones but not on integrated speakers. 

Many posters have pointed out that the solution to the problem is often as simple as adding a line at the end of /etc/modprobe.d/alsa-base along the lines of

```
options snd-hda-intel model=xyz
```


Lenovo	???
```
options snd-hda-intel model=laptop-eapd
```
[http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel](http://ubuntuforums.org/showthread.php?t=332472&highlight=snd_hda_intel) #2



I can confirm this solution works on a Lenovo Y400 with Intel ICH7 (82801g controller) using  Ubuntu 6.10 i386 default install. This is an Asian market only laptop but it is based on the very common Lenovo 3000 series. I added the line and rebooted and  now have perfect controllable sound from the onboard speakers and/or from the line out/headphone minijack. It sounds truly excellent, I never heard a laptop with sound this good before. So thanks very much for the tip....I already lost one whole nights sleep trying to fix this different ways  and finally it's time for a beer and a long rest :) 

btw on XP the  Windows driver installation from the official Lenovo install disk is actually pretty flaky too, problems recognising the hardware, problems copying the system files to the right place and so on :lolflag: and at the end you get a feeble sound. The Alsa driver once configured actually takes advantage of the hardware which is a mini subwoofer as well as the usual laptop stereo pair :)

---

### Post by jackn on 2007-04-05
When I try to apply this modification on my Kubuntu-run laptop, I still don't get sound.

The specific line I added is 

```
options snd-hda-intel position_fix=1 model=3stack
```,[as suggested]("http://www.rothlaender.net/a8js.html") by a Gentoo user.


I think the failure to get sound in spite of the addition of this line might be related to the fact that KDE uses its own sound control, and that I need to run Alsa. I've tried doing that off of the 'sound' section of the 'system settings', but no luck.

Am I right about this and, if so, how can I get Alsa to run sound in Kubuntu?

I was told I needed to run alsaconf to have Alsa control sound.
I don't have 'alsaconf' ('command not found'). This seems to be a common occurrence on the net, but I haven't found a solution.
I've downloaded [alsaconf ]("/etc/modules.d/alsa")from the alsa.org site. Upon running it (it's a shell script), I got an error message...

I've also read that alsaconf is s a part of alsa-utils. Yet, I cannot find alsaconf anywhere near an alsa-utils directory. When I try to apt-get install alsa-utils, I'm told it's already the newest version.

While looking for alsaconf, however, I've found the alsactl file. It allows you to run
```

alsactl restore
```

which, miraculously, resotored sound to my laptop.

However, it also spat out these error messages:```

:~$ alsactl restore
alsactl: set_control:894: warning: name mismatch (IEC958 Playback Con Mask/Channel Mode) for control #29
alsactl: set_control:896: warning: index mismatch (0/0) for control #29
alsactl: set_control:994: bad control.29.value type
```

I also can't control the volume with the KDE desktop mixer or with the media buttons of my laptop...

I do know that the sound I get depends on the addition of the above line, as commenting it out (with update-modules and reboot) leads to loss of sound which 'alsactl restore' fails to restore.

In short, great improvement with the addition of the suggested line, but I feel that I'm far from getting the full power of the Intel HD audio sound card.

Could anyone help?
Jackn

---

### Post by PaoloVIP on 2007-04-07
**Packard Bell V7900 ALC260 Solution:**

[http://forum.ubuntu-it.org/index.php?topic=39574.0](http://forum.ubuntu-it.org/index.php?topic=39574.0)

---

### Post by milou on 2007-05-19
Soundcard in D900t laptop :

you must use the following option to get sound working properly :

options snd-hda-intel model=clevo probe_mask=1


Eric


PS : model is not so important and other models will not prevent sound from working , but probe_mask=1 IS necessary !!!

---

### Post by kpagan on 2007-07-08
Well I have a **Toshiba Tecra A8-103** laptop and I installed the Ubuntu Feisty Fawn 64-bit Linux.
I couldn't hear sound from the integrated speakers too.
I tried options 
```
snd-hda-intel model=3stack
``` 
and 
```
options snd-hda-intel probe_mask=8 model=3stack
``` 
that was referring to Toshiba laptops with no effects.
When I type 
```
lspci | grep Audio
``` the output it produces is ```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

When I typed 
```
aplay -l
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
or something like that. Anyway the important part is **[ALC262 Analog]**
Then I read the solution that **eggdeng** posted.
I searched for [ALC262 Analog] in **/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt**
and the portion of the text was 
```
	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  benq		Benq ED8
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)
```

It seems here that I should set my model as **fujitsu**
So I edited **/etc/modprobe.d/alsa-base** and entered
```
options snd-hda-intel model=fujitsu
```
and now I can hear sound from the integrated speakers as well.

Thanks eggdeng. That post was the most useful

---

### Post by THROBiX on 2007-07-22
:o Cool!
Right now, I managed to fix the -switch between minijack or internal speaker- mode on my Quanta MW1 laptop!
First of, sound came only through the internal speakers... 
Later I added model=lg, then I only got sound through the minijack (I use headphones all day). Right now I added model=lg-lw - and guess what? The internal speakers works. If I plug in the headphones, the internal speakers turns off and the minijack goes on! Wee! :popcorn:
Btw, it's an (Realtek?) ALC880 chipset + Ubuntu 7.04.

---

### Post by thesoothsayer on 2007-07-22
For the ASUS A8Fm laptop that I have.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspic -vnn
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device [1043:1443]
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

cat /proc/asound/card0/codec#*
Codec: Analog Devices AD1986A
Address: 0
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500



I used this setting:
> options snd-hda-intel position_fix=0 model=3stack


Which is weird because when I first installed edgy in Feb 2007, I couldn't get 3stack to work and used laptop-eapd. Then one day, laptop-eapd couldn't work and I changed to 3stack with position_fix=1 and that was the only thing that I remember worked. Now, position_fix=1 can't work and position_fix=0 can. I checked the software that I've installed and none of them look like they could affect the drivers and I've also recompiled the latest Alsa drivers but they suddenly stopped working with the old settings one fine day (which was yesterday). Well, just glad that it's working now with the new option settings.

If one fine day you wake up and this setting can't work anymore, my suggestion would be to first cycle through the settings before looking at other areas.

Currently, options for "model" in this card are:
6stack
3stack
laptop
laptop-eapd
ultra

And options for "position_fix" are:
0
1
2
3

---

### Post by st0nes on 2007-07-25
I'm getting to the end of my tether with this sound problem.  I've been trying out all sorts of combinations in the alsa-base file, but whatever I do seems to make no difference.  The problem is that the sound through the headphones is way too low in volume to be usable.  I can just barely hear anything at all.  Speaker is working normally, but that's no use because I like to listen to music at work.  Here is the ouput of aplay:-
```
mark@mark-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Here is the codec info:-
```
mark@mark-laptop:~$ cat /proc/asound/card0/codec#*
Codec: Generic 1106 ID 1708
Address: 0
Vendor Id: 0x11061708
Subsystem Id: 0x15585408
Revision Id: 0x100700
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x10 [Audio Output] wcaps 0x411: Stereo
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x11 [Audio Output] wcaps 0x411: Stereo
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x12 [Audio Output] wcaps 0x411: Stereo
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x13 [Audio Output] wcaps 0x411: Stereo
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
Node 0x14 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
Node 0x15 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x14 0x14]
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
  Connection: 1
     0x18
Node 0x16 [Audio Input] wcaps 0x100311: Stereo Digital
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0xa]: 16 24
    formats [0x5]: PCM AC3
  Connection: 1
     0x26
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x06, mute=1
  Amp-In vals:  [0x1f 0x1f] [0x08 0x08] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 6
     0x10 0x24 0x1d 0x1e 0x21 0x13
Node 0x18 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 5
     0x17* 0x24 0x1d 0x1e 0x21
Node 0x19 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x11
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x1c [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x410110f2: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x19
Node 0x1d [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
  Pin Default 0x01a19026: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
Node 0x1e [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
  Pin Default 0x0181302e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x00:
  Connection: 1
     0x19
Node 0x1f [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x17
Node 0x20 [Pin Complex] wcaps 0x40010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x1b, nsteps=0x1b, stepsize=0x06, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081c: OUT HP Detect
  Pin Default 0x022140f0: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x17
Node 0x21 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x08334: IN OUT Detect
  Pin Default 0x02a190f0: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x00:
  Connection: 1
     0x1b
Node 0x22 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x410160f1: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
Node 0x23 [Pin Complex] wcaps 0x400101: Stereo
  Pincap 0x0814: OUT Detect
  Pin Default 0x410120f4: [N/A] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
  Pin-ctls: 0x00:
  Connection: 1
     0x1b
Node 0x24 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x99330127: [Fixed] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x25 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x074411f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = RCA, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x14
Node 0x26 [Pin Complex] wcaps 0x400201: Stereo Digital
  Pincap 0x0810030: IN OUT EAPD
  Pin Default 0x47c421f0: [N/A] SPDIF In at Ext Rear Panel
    Conn = RCA, Color = Grey
  Pin-ctls: 0x00:
Node 0x27 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x14, stepsize=0x06, mute=1
  Amp-In vals:  [0x80 0x80]
  PCM:
    rates [0x440]: 48000 192000
    bits [0xa]: 16 24
    formats [0x1]: PCM
  Power: 0x0
  Connection: 1
     0x21

```
And here is my alsa-base file:-
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Added this in a vain attempt to sort out headphone problem (low volume). Bug logged with alsa. MW 18/7/2007.
options snd-hda-intel index=0 model=hp-bpc probe_mask=1

```
So far, I have tried:-
hp
thinkpad
laptop
laptop-eapd
3stack
3stack-dig
5stack
viao
viao-ar
basic
allout
minimal
acer
arima
fujitsu
benq

None of these models change anything -- they all produce the same non-result.  If anyone out there has the same hardware and have got their sound working properly, I would be enourmously grateful to know how to fix mine.  Another thing: the "front" slider in alsamixer seems to control the headphone volume and the "headphone" slider controls the speakers.

Any assistance will be gratefully received.  Please let me know if you need any further info.

---

### Post by eggdeng on 2007-07-28
Your card is HDA VIA, not HDA Intel like the ones addressed on this thread. You might try doing  a forum search for HDA VIA VT82xx.

---

### Post by Luther Blissett on 2007-08-09
Eggdeng, kpagan  and the others, thanks so much for making my Tecra A8 play sounds. You are stars.
I now face the problem of the onboard speakers that don't mute when I plug the jack in. Has any of you already solved the issue of jack sensing for this hardware (with Feisty)?
Cheers!

---

### Post by julian67 on 2007-08-09
I had the same problem after upgrading from the original feisty kernel. try reverting back to 2.6.20-15 and your mod to alsa-base may work ok.

---

### Post by jackn on 2007-08-09
In my hands, Luther, running Feisty on Asus a8js, what works best, and, in particular, what allows switching between the headphones and the speakers upon plugigin in the headphones is the line

```
options snd-hda-intel model=3stack
```

My kernel:
```
~$ uname -a
Linux box_name 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

"position_fix=1" has no effect.

"model=laptop" allows listening to the speakers, but the headphone switch does not occur.

In other people's hands, other settings work well, such as 'laptop-eapd' ([here]("http://forum.ubuntu-fr.org/viewtopic.php?id=114268"), if you read French). This latter setting has been reported to work with the same laptop model as mine. 
Sometimes a reboot, not only a restart of the daemon, is apparently necessary.



Hope this helps. Let us know, and good luck.

jackn

---

### Post by Luther Blissett on 2007-08-11
Thanks for your suggestion Jackn,
My Toshiba Tecra A8 has the ALC262 chip which I reckon is different to that of your Asus. The model=3stack did not work for me (I tried it though...).
So far the only breakthrough was kpagan's suggestion to use model=fujitsu. That made the speakers work but no jack sensing yet.
Cheers,
Luther

---

### Post by Pixman on 2007-08-11
Hi, I have a kinda similar problem.
When I turn acpi off, the sound works but my WiFi doesn't do anymore.

I tried every configuration possible in the /etc/modprobe.d/alsa-base file and even compiled alsa again.

I can only choose between having no wifi (which I desperately do need) and not having several  other functions (like turning off)    OR    having no sound and all other functions.

It's an Asus Aspire 5310.

---

### Post by jackn on 2007-08-11
Yes, of course, Luther.

[This post]("http://forum.ubuntu-fr.org/viewtopic.php?pid=950776") has a list of all the possible values of 'model' in alsa-base, according to make.

Just go system - preferences - sound. There, under 'Default Mixer Tracks', it says 'device'. This is probably set to alsa in your case. The dropdown menu, however, shows a string associated with the OSS mixer. This string can be found in the table in the above thread. Under your string, all the possible values of 'model' are listed.

There are other options in the 'model' line in alsa-base, of course, but going through these different values is a start.

Forgive me if this is all old hat to you.

jackn

---

### Post by dä_oll_klaus on 2007-08-14
> **Pixman said:**
> Hi, I have a kinda similar problem.
When I turn acpi off, the sound works but my WiFi doesn't do anymore.

I tried every configuration possible in the /etc/modprobe.d/alsa-base file and even compiled alsa again.

I can only choose between having no wifi (which I desperately do need) and not having several  other functions (like turning off)    OR    having no sound and all other functions.

It's an Asus Aspire 5310.

Yes, I had exactly the same problem ... trying kernel options pci=noacpi or pci=assign-buses.
Nothing did the job.

I finally ended up compiling hda-intel into the kernel - not as a module.
And suddenly everything worked fine!!!!

I'm using a DELL D830 which comes with a SIGMA STAC 9205.

dä_oll_klaus

---

### Post by musicarvind on 2007-08-16
> **MadeR said:**
> use the sudo command

for example ```

sudo vim /etc/alsa

```

if you are using kde and you need a window application (for example "kate") use kdesu instead.
there is a similar command for gnome, if I am not wrong gtksudo or gsudo, but I do not remember the name.

I still cant figure out this part.  com just tells me that i do not have permissions to edit this file. can someone tell me in lay man terms. slowly? step by step? please? 

i just keep geting this sharp hissing sound and whenever i touch any volume control, it goes silent.

---

### Post by musicarvind on 2007-08-17
> **musicarvind said:**
> I still cant figure out this part.  com just tells me that i do not have permissions to edit this file. can someone tell me in lay man terms. slowly? step by step? please? 

i just keep geting this sharp hissing sound and whenever i touch any volume control, it goes silent.


can anyone please help me with this?

---

### Post by musicarvind on 2007-08-17
> **musicarvind said:**
> can anyone please help me with this?

ok solved it.  used this in terminal to edit the file. 

gksudo gedit /etc/modprobe.d/alsa-base

and then it worked with putting this in the alsa-base file.

options snd-hda-intel model=3stack

thank you everyone :) :KS

---

### Post by el_Salmon on 2007-08-27
> **thesoothsayer said:**
> For the ASUS A8Fm laptop that I have.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspic -vnn
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device [1043:1443]
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

cat /proc/asound/card0/codec#*
Codec: Analog Devices AD1986A
Address: 0
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500


Which is weird because when I first installed edgy in Feb 2007, I couldn't get 3stack to work and used laptop-eapd. Then one day, laptop-eapd couldn't work and I changed to 3stack with position_fix=1 and that was the only thing that I remember worked. Now, position_fix=1 can't work and position_fix=0 can. I checked the software that I've installed and none of them look like they could affect the drivers and I've also recompiled the latest Alsa drivers but they suddenly stopped working with the old settings one fine day (which was yesterday). Well, just glad that it's working now with the new option settings.

If one fine day you wake up and this setting can't work anymore, my suggestion would be to first cycle through the settings before looking at other areas.

Currently, options for "model" in this card are:
6stack
3stack
laptop
laptop-eapd
ultra

And options for "position_fix" are:
0
1
2
3

Hi thesoothsayer,

I have a new Asus laptop, z99f model, with A8FM motherboard and the same audio card that you 
I have added this line:
```
options snd-hda-intel position_fix=0 model=3stack
```

but it doesn't work fine:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
The sound in integrated speakers is very low and output line doesn't work. I have setup Kubuntu Gutsy (kernel 2.6.22-10-generic)

---

### Post by Guyver1 on 2007-08-28
ok i have the ALC885 chip, my options are:

ALC882/885
3stack-dig	3-jack with SPDIF I/O
6stck-dig	6-jack digital with SPDIF I/O
arima		Arima W820Di1
auto		auto-config reading BIOS (default)

before i used the extra line in alsa-base sound would only come out of the headphones.

when i added the extra line sound only comes out of the built in speakers regardless of which of the above i use.

any got any idea's what i can do to get the 'mute speakers on headphone input' working??

cheers

---

### Post by Guyver1 on 2007-08-31
ok I've tried many a configuration and still cant get the headphone jack switch to work :(

Im on an Alienware m9750 with the Realtek ALC885 (Intel ALC882) HD Audio chipset.

alplay -l gives me:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
guyver1@ubuntu:~$ 

```


The Alsa Configuration file shows the following for my chip:
```

ALC882/885
3stack-dig	3-jack with SPDIF I/O
6stck-dig   	6-jack digital with SPDIF I/O
 arima		Arima W820Di1
auto		auto-config reading BIOS (default)

```

my current alsa-base shows like this:
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto position_fix=1

```


3stack-dig	Laptop speakers work, headphone switch doesnt switch off speakers
6stck-dig   	speakers dont work
 arima		Laptop speakers work, headphone switch doesnt switch off speakers
auto                         speakers dont work

ive tried all of those with position_fix=1 and nothing works :(

how many position fix options are there? what does the position_fix actually do and how does it relate to the alsa driver?

Can anyone help me get the damn headphone/speaker switching working please !!! :)

---

### Post by nduper on 2007-08-31
Hallo everybody,
I have a Toshiba L30-10T and I am going mad trying to make work my audio as all of you around here :). I tried many different distros and now I am trying Ubuntu studio. 
This is the way (VERY WEIRD) how my audio works (both front and phones):
add "options snd-hda-intel probe_mask=8 model=3stack" in /etc/modprobe.d/alsa-base
reboot
with this option I have only PCM audio control
open again alsa-base
comment or cancel "options snd-hda-intel probe_mask=8 model=3stack"
turn off the computer
boot... and there it is :-D :guitar: front audio works, headphones are controlled by surround sliders and front audio is off when minijack is inserted.
WHAT CAN I SAY? SILLY!
Andybody has an idea what is going on?

---

### Post by nduper on 2007-09-01
I forgot to say, maybe it was not clear, I have to do this operation every time I turn on the computer :lolflag:, if I want to have the audio working. If not I have only front right audio and the headphones become the computer loudspeaker (the beep one :)). 
I hope that this experience will be useful to somebody with more knowledge to fix this so annoying problem with SB450.

This is my lspci:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by Lord Illidan on 2007-09-01
This might help :

```
  Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
        ATI SB450, SB600, RS600,
        VIA VT8251/VT8237A,
        SIS966, ULI M5461

    model    - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    single_cmd  - Use single immediate commands to communicate with
        codecs (for debugging only)
    enable_msi    - Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

      Model name    Description
      ----------    -----------
    ALC880
      3stack    3-jack in back and a headphone out
      3stack-digout    3-jack in back, a HP out and a SPDIF out
      5stack    5-jack in back, 2-jack in front
      5stack-digout    5-jack in back, 2-jack in front, a SPDIF out
      6stack    6-jack in back, 2-jack in front
      6stack-digout    6-jack with a SPDIF out
      w810        3-jack
      z71v        3-jack (HP shared SPDIF)
      asus        3-jack (ASUS Mobo)
      asus-w1v    ASUS W1V
      asus-dig    ASUS with SPDIF out
      asus-dig2    ASUS with SPDIF out (using GPIO2)
      uniwill    3-jack
      fujitsu    Fujitsu Laptops (Pi1536)
      F1734        2-jack
      lg        LG laptop (m1 express dual)
      lg-lw        LG LW20/LW25 laptop
      tcl        TCL S700
      clevo        Clevo laptops (m520G, m665n)
      test        for testing/debugging purpose, almost all controls can be
            adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y
      auto        auto-config reading BIOS (default)

    ALC260
      hp        HP machines
      hp-3013    HP machines (3013-variant)
      fujitsu    Fujitsu S7020
      acer        Acer TravelMate
      basic        fixed pin assignment (old default model)
      auto        auto-config reading BIOS (default)

    ALC262
      fujitsu    Fujitsu Laptop
      hp-bpc    HP xw4400/6400/8400/9400 laptops
      hp-bpc-d7000    HP BPC D7000
      benq        Benq ED8
      hippo        Hippo (ATI) with jack detection, Sony UX-90s
      hippo_1    Hippo (Benq) with jack detection
      basic        fixed pin assignment w/o SPDIF
      auto        auto-config reading BIOS (default)

    ALC882/885
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      arima        Arima W820Di1
      macpro    MacPro support
      w2jc        ASUS W2JC
      auto        auto-config reading BIOS (default)

    ALC883/888
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack digital with SPDIF I/O
      3stack-6ch    3-jack 6-channel
      3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
      6stack-dig-demo  6-jack digital for Intel demo board
      acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
      medion    Medion Laptops
      targa-dig    Targa/MSI
      targa-2ch-dig    Targs/MSI with 2-channel
      laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
      auto        auto-config reading BIOS (default)

    ALC861/660
      3stack    3-jack
      3stack-dig    3-jack with SPDIF I/O
      6stack-dig    6-jack with SPDIF I/O
      3stack-660    3-jack (for ALC660)
      uniwill-m31    Uniwill M31 laptop
      toshiba    Toshiba laptop support
      asus        Asus laptop support
      asus-laptop    ASUS F2/F3 laptops
      auto        auto-config reading BIOS (default)

    ALC861VD/660VD
      3stack    3-jack
      3stack-dig    3-jack with SPDIF OUT
      6stack-dig    6-jack with SPDIF OUT
      3stack-660    3-jack (for ALC660VD)
      lenovo    Lenovo 3000 C200
      auto        auto-config reading BIOS (default)

    CMI9880
      minimal    3-jack in back
      min_fp    3-jack in back, 2-jack in front
      full        6-jack in back, 2-jack in front
      full_dig    6-jack in back, 2-jack in front, SPDIF I/O
      allout    5-jack in back, 2-jack in front, SPDIF out
      auto        auto-config reading BIOS (default)

    AD1884
      N/A

    AD1981
      basic        3-jack (default)
      hp        HP nx6320
      thinkpad    Lenovo Thinkpad T60/X60/Z60
      toshiba    Toshiba U205

    AD1983
      N/A

    AD1984
      basic        default configuration
      thinkpad    Lenovo Thinkpad T61/X61

    AD1986A
      6stack    6-jack, separate surrounds (default)
      3stack    3-stack, shared surrounds
      laptop    2-channel only (FSC V2060, Samsung M50)
      laptop-eapd    2-channel with EAPD (Samsung R65, ASUS A6J)
      ultra        2-channel with EAPD (Samsung Ultra tablet PC)

    AD1988
      6stack    6-jack
      6stack-dig    ditto with SPDIF
      3stack    3-jack
      3stack-dig    ditto with SPDIF
      laptop    3-jack with hp-jack automute
      laptop-dig    ditto with SPDIF
      auto        auto-config reading BIOS (default)
    
    Conexant 5045
      laptop    Laptop config 
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    Conexant 5047
      laptop    Basic Laptop config 
      laptop-hp    Laptop config for some HP models (subdevice 30A5)
      laptop-eapd    Laptop config with EAPD support
      test        for testing/debugging purpose, almost all controls
            can be adjusted.  Appearing only when compiled with
            $CONFIG_SND_DEBUG=y

    STAC9200/9205/9254
      ref        Reference board

    STAC9220/9221
      ref        Reference board
      3stack    D945 3stack
      5stack    D945 5stack + SPDIF
      intel-mac-v1    Intel Mac Type 1
      intel-mac-v2    Intel Mac Type 2
      intel-mac-v3    Intel Mac Type 3
      intel-mac-v4    Intel Mac Type 4
      intel-mac-v5    Intel Mac Type 5
      macmini    Intel Mac Mini (equivalent with type 3)
      macbook    Intel Mac Book (eq. type 5)
      macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
      macbook-pro    Intel Mac Book Pro 2nd generation (eq. type 3)
      imac-intel    Intel iMac (eq. type 2)
      imac-intel-20    Intel iMac (newer version) (eq. type 3)

    STAC9202/9250/9251
      ref        Reference board, base config
      m2-2        Some Gateway MX series laptops
      m6        Some Gateway NX series laptops
      pa6        Gateway NX860 series

    STAC9227/9228/9229/927x
      ref        Reference board
      3stack    D965 3stack
      5stack    D965 5stack + SPDIF

    STAC9872
      vaio        Setup for VAIO FE550G/SZ110
      vaio-ar Setup for VAIO AR

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    Note 2: If you get click noises on output, try the module option
        position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
        register value without FIFO size correction as the current
        DMA pointer.  position_fix=2 will make the driver to use
        the position buffer instead of reading SD_LPIB register.
        (Usually SD_LPLIB register is more accurate than the
        position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    MORE NOTES ON "azx_get_response timeout" PROBLEMS:
    On some hardwares, you may need to add a proper probe_mask option
    to avoid the "azx_get_response timeout" problem above, instead.
    This occurs when the access to non-existing or non-working codec slot
    (likely a modem one) causes a stall of the communication via HD-audio
    bus.  You can see which codec slots are probed by enabling
    CONFIG_SND_DEBUG_DETECT, or simply from the file name of the codec
    proc files.  Then limit the slots to probe by probe_mask option.
    For example, probe_mask=1 means to probe only the first slot, and
    probe_mask=4 means only the third slot.

    The power-management is supported.
```

---

### Post by nduper on 2007-09-01
I'm sorry. I don't understand what I should do.
This is my alsa-base:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
#options snd-hda-intel probe_mask=8 model=3stack

Thank you if you can help me, I've lost days and days in looking for the solution :confused:

---

### Post by Dave Crowhurst on 2007-09-01
I have tried changing model=ACER without success :(

lspci | grep Audio
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is my alsa-base
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=acer
options snd-hda-intel probe_mask=1
```

Any ideas on a solution?

---

### Post by nduper on 2007-09-01
Ok, I've solved this problem by adding these to alsa-base:
options snd-hda-intel model=toshiba probe_mask=1
options snd_hda_intel model=uniwill-m31

Looking for the solution for the "[ 25.792704] hda_codec: invalid dep_range_val 0:7fff" I found one spanish forum where the expert was saying to add these two options. I did it and now I dont have this message (dmesg) (hda_codec: invalid dep_range) and my audio works ok.
To be honest it is not perfect because I have surround audio options and this is not the hw I have on my laptop (Toshiba L30-10T) but anyway I am happy :).
I hope this will help other people

---

### Post by thesoothsayer on 2007-10-21
This is getting tiring. Seems like I need to change the setting every 3 months or so.

Now position_fix=8 works when just a while back only 0-3 could output anything. Any other position just causes the sound to die off after a few minutes now.

options snd-hda-intel position_fix=8 model=3stack

> 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

lspic -vnn
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
Subsystem: ASUSTeK Computer Inc. Unknown device [1043:1443]
Flags: bus master, fast devsel, latency 0, IRQ 23
Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

cat /proc/asound/card0/codec#*
Codec: Analog Devices AD1986A
Address: 0
Vendor Id: 0x11d41986
Subsystem Id: 0x10431443
Revision Id: 0x100500


Which is weird because when I first installed edgy in Feb 2007, I couldn't get 3stack to work and used laptop-eapd. Then one day, laptop-eapd couldn't work and I changed to 3stack with position_fix=1 and that was the only thing that I remember worked. Now, position_fix=1 can't work and position_fix=0 can. I checked the software that I've installed and none of them look like they could affect the drivers and I've also recompiled the latest Alsa drivers but they suddenly stopped working with the old settings one fine day (which was yesterday). Well, just glad that it's working now with the new option settings.

If one fine day you wake up and this setting can't work anymore, my suggestion would be to first cycle through the settings before looking at other areas.

Currently, options for "model" in this card are:
6stack
3stack
laptop
laptop-eapd
ultra

And options for "position_fix" are:
0
1
2
3

---

### Post by julian67 on 2007-10-21
> **thesoothsayer said:**
> This is getting tiring. Seems like I need to change the setting every 3 months or so.

Now position_fix=8 works when just a while back only 0-3 could output anything. Any other position just causes the sound to die off after a few minutes now.

options snd-hda-intel position_fix=8 model=3stack

A kernel upgrade or alsa upgrade probably are why you need to mess about with this sometimes. Once you have it working as desired you can go into synaptic and lock the kernel version and alsa version so they don't get updated, but you need to check security advisories and be sure that you're happy keeping your kernel version when security updates are made available.

---

### Post by rafar on 2007-11-12
Hi. Im trying to get my headphone switch to work when I plug in. It seems the internal speakers dont turn off when i plug headphones in. I've tried all of the above solutions with modifying alsa-base file, but none work.
My card is ALC660 VD the Realtech HD one. I'm using Gutsy on an Asus F3KA laptop.
If possible is there a way to completely shut off the internal speakers on my laptop.
Thanks









/*****
The stone age didn't end because we ran out of stones.
*****/

---

### Post by maniqui on 2007-12-04
FYI:
in an MSI Laptop model V330, I was having the following issue: when plug-in headphones/external speakers, the internal laptop speaker was being muted.

"aplay -l" output:
```
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
```


This worked for me:
On /etc/modprobe.d/alsa-base, I added at the end:

```
options snd-hda-intel model=targa-dig
```

I will also try other options to see what happens.

**Edit:** 

it also works (and think its better) with:

```
options snd-hda-intel model=targa-2ch-dig
```

---

### Post by kpagan on 2008-02-05
> **eggdeng said:**
> 
....
Toshiba Tecra A8-103
```
options snd-hda-intel probe_mask=8 model=fujitsu
```
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)
#14


My friend eggdeng.
I tried your suggestion above and my soundcard was not recognized at all.
I had posted that the solution for the Toshiba Tecra A8-103 was
```
options snd-hda-intel model=fujitsu
```

So I suggest to remove the **probe_mask=8** in order to prevent confusion to other users.

---

### Post by Raikerson on 2008-02-05
I have a acer travelmate 5520, and can't get my headphone jack to work at all. Laptop speakers work.
lspci: ATI Technologies Inc SBx00 Azalia
cat /proc/asound/card0/codec: Realtek ID  268
Running ubuntu 7.10amd64

My alsa-base has "options snd-hda-intel model=acer", and I've tried with "model=3stack" without luck.
Downloaded realtek drivers and compiled/installed them, still no go.
Downloaded alsa drivers and compiled/installed them, didnt work either.
Followed various guides like [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but still no luck.

Anyone have a clue as to what I should do to get my headphone jack working?

---

### Post by Raikerson on 2008-02-05
> **Raikerson said:**
> I have a acer travelmate 5520, and can't get my headphone jack to work at all. Laptop speakers work.
lspci: ATI Technologies Inc SBx00 Azalia
cat /proc/asound/card0/codec: Realtek ID  268
Running ubuntu 7.10amd64

My alsa-base has "options snd-hda-intel model=acer", and I've tried with "model=3stack" without luck.
Downloaded realtek drivers and compiled/installed them, still no go.
Downloaded alsa drivers and compiled/installed them, didnt work either.
Followed various guides like [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but still no luck.

Anyone have a clue as to what I should do to get my headphone jack working?

Hmm...I got the gtk-setuid message when logging on so did a reinstall using a custom live cd (created with remastersys about one hour before getting the deathmessage), after reinstall I got whole bunch more sliders in volume controll and everything works, mic, headphone jack, automute, etc.
If someone would care to explain this I'd be grateful :).

---

### Post by clovis_ll on 2008-02-05
> **Luther Blissett said:**
> Thanks for your suggestion Jackn,
My Toshiba Tecra A8 has the ALC262 chip which I reckon is different to that of your Asus. The model=3stack did not work for me (I tried it though...).
So far the only breakthrough was kpagan's suggestion to use model=fujitsu. That made the speakers work but no jack sensing yet.
Cheers,
Luther

i am seeing alc262 also on my sony vaio cr320. so if i used the "..nodel=fujitsu" patch, will it work?
the wierd thing is that i have a volume slider without sound coming out.. (sorry newbie)
 ):P

---

### Post by kpagan on 2008-02-06
> **clovis_ll said:**
> i am seeing alc262 also on my sony vaio cr320. so if i used the "..nodel=fujitsu" patch, will it work?
the wierd thing is that i have a volume slider without sound coming out.. (sorry newbie)
 ):P

Well try it. Don't forget to reboot.
If everything works OK then leave it else put the old value back and restart.

---

### Post by AFCB on 2008-02-16
i friends
sorry for the borring

i have an lg-lw65 portable
so i have installed ubuntu 7.10 on my laptop.
but i can make work the sound on the internal speakers
the sound playes on the headphones but not on the speakers

i have readed the intire thread.

my soundcard is, according with de aplay -l:
[I]
placa 0: Intel [HDA Intel], dispositivo 0: CMI9880 [CMI9880]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 6: Si3054 Modem [Si3054 Modem]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0[/I]

i tried to put the line:

*options snd-hda-intel model=minimal*

on the alsa-base file

but still no sound on the speakers

i have already tried:

  [I]        minimal	3-jack in back 
	  min_fp	3-jack in back, 2-jack in front 
	  full		   6-jack in back, 2-jack in front 
	  full_dig	  6-jack in back, 2-jack in front, SPDIF I/O 
	  allout	  5-jack in back, 2-jack in front, SPDIF out 
	  auto		 auto-config reading BIOS (default)
[/I]

but still not working

i'm tired of trying many tips but i can put sound on speakers

my alsa-base version are the lastest 1.1.16

waiting

sorry for the english..i'm portuguese

regards friends

André Fernandes
Portugal

---

### Post by eggdeng on 2008-02-16
Haven't you tried
```
options snd-hda-intel model=lg
```
This works for me (on an LG P1 Express Dual). Don't forget to reboot.

---

### Post by AFCB on 2008-02-16
> **eggdeng said:**
> Haven't you tried
```
options snd-hda-intel model=lg
```
This works for me (on an LG P1 Express Dual). Don't forget to reboot.


have you the CMI9880??

regards and thanks

i will test your sugestion

---

### Post by AFCB on 2008-02-16
> **eggdeng said:**
> Haven't you tried
```
options snd-hda-intel model=lg
```
This works for me (on an LG P1 Express Dual). Don't forget to reboot.

i friend

i have tested with *lg* and nothing

i have tested one more time with *minimal* and nothing

what i have to do is only change the alsa-base file and reboot???

no more adjustes???

i need help friends:(:(
i want to kiss windows ass:lolflag:

but i have to have sound:(:(:(

only sound are wrong at the moment:(:(

---

### Post by eggdeng on 2008-02-17
My card is  ALC880. It seems that Vista users have been having problems with the sound on the lg-lw65 too. I think you have done all you can. Perhaps you should file a bug report at
    [https://bugtrack.alsa-project.org/bugs/]("https://bugtrack.alsa-project.org/bugs/")
Sorry not to have been of more help.

---

### Post by thesoothsayer on 2008-03-01
Just in case anyone's using Asus A8Fm, the new working configuration for me in Gutsy Gibbon is:

options snd-hda-intel position_fix=1 model=3stack

The default configuration works but stops when the alsamixer volume is adjusted. This setting allows it to continue working even when the mixer is adjusted.

---

### Post by bubonic1347 on 2008-03-12
> **julian67 said:**
> A kernel upgrade or alsa upgrade probably are why you need to mess about with this sometimes. Once you have it working as desired you can go into synaptic and lock the kernel version and alsa version so they don't get updated, but you need to check security advisories and be sure that you're happy keeping your kernel version when security updates are made available.

So it seems I re-install Mythbuntu again and lock things down. I have no idea how to lock things down.

---

### Post by julian67 on 2008-03-12
> **bubonic1347 said:**
> So it seems I re-install Mythbuntu again and lock things down. I have no idea how to lock things down.

you can do it in synaptic. When you have everything set up right so your sound works then you can use synaptic, search for your kernel (linux-image) and alsa version and then  select the package,  then in the menu: Package>Lock Version. Locked packages do not get updated so you need to be aware of any security patches for the kernel that might be important for you and be prepared occasionally to upgrade the kernel and fix your sound again. You'll also need to unlock the packages if you want to do a distribution upgrade. 

You might want to back up your root partition to a  disk image so it's easily restored to current working state in case you make some update/upgrade you're not happy with. clonezilla-live is good for this, search these forums or just google to find out more about that.

---

### Post by Sergeant_Pony on 2008-03-17
I have a toshiba satellite A105-S2131 and I can only get partial sound on login using:
options snd-hda-intel model=auto

is is what aplay -l says:
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Any ideas?
Help please! :)
Thanks, Sergeant_Pony

---

### Post by Sergeant_Pony on 2008-03-17
I have a toshiba satellite A105-S2131 and I can only get partial sound on login using:
options snd-hda-intel model=auto

is is what aplay -l says:
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0

---

