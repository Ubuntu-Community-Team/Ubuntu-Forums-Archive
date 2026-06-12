---
title: "Sound &quot;pops&quot; just before and after audio playback"
date: 2011-05-11
forum: Hardware
---

### Post by Willard on 2011-05-11
Hi folks,

Whenever I play sound on my laptop, the sound "pops" just before playback, just like in the old days when you started a DOS game. A few seconds after playback, the sound pops again, albeit very faintly.

This problem started after I major-upgraded from 10.04 to 11.04 a few days ago.

Could you guys help me fix this issue?

edit: The sound also pops before and after I adjust my volume (with alsamixer, or with my laptop hotkeys).

My speakers are not to blame; my headset has the same issue.

I have an Asus F8SA laptop.

If you want any other specification, then I will happily provide it.

Cheers,
Willard.

---

### Post by sanderd17 on 2011-05-11
In my case, the sound pops when I change the volume and use the line-out (not the internal speakers). It doesn't matter if I user headphones or external speakers so they are not the problem. It has been that way since 10.10 and I never found something to repair it.

---

### Post by Willard on 2011-05-11
> **sanderd17 said:**
> In my case, the sound pops when I change the volume and use the line-out (not the internal speakers). It doesn't matter if I user headphones or external speakers so they are not the problem. It has been that way since 10.10 and I never found something to repair it.

Ah; an omission in my problem description. We have the same problem. It is the sound coming out of my line-out that pops. I cannot hear the "pop" in my internal speakers.

---

### Post by lidex on 2011-05-11
What is this terminal output:
```
cat /etc/modprobe.d/alsa-base.conf
```
Terminal="Applications->Accessories->Terminal"

---

### Post by sanderd17 on 2011-05-12
This is my output:

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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


```

---

### Post by NightwishFan on 2011-05-12
I am no expert but this may be part of the sound cards power save feature not liking pulseaudio.

---

### Post by lidex on 2011-05-12
@Willard
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Willard on 2011-05-21
> **lidex said:**
> What is this terminal output:
```
cat /etc/modprobe.d/alsa-base.conf
```
Terminal="Applications->Accessories->Terminal"
```
willard@naglfar: ~
$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```
> **NightwishFan said:**
> I am no expert but this may be part of the sound cards power save feature not liking pulseaudio.I suspected power saving was involved. Do you happen to know how to disable this feature?
> **lidex said:**
> @Willard
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
I put it [here]("http://willard.madscience.dk/alsa-info.txt.rXVCa0ner9"). The file will remain there for at least 1 week.

---

### Post by lidex on 2011-05-22
I'd like to see this output please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by Willard on 2011-05-22
> **lidex said:**
> I'd like to see this output please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
I ran the command twice, before and after firing up a process which uses my sound devices.
```
willard@naglfar: ~
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1112 F.... slmodemd
                     willard    2039 F.... pulseaudio
                     willard    4102 F.... alsamixer
/dev/snd/pcmC0D6c:   Slmodemd   1112 F.... slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1112 F.... slmodemd
/dev/snd/seq:        timidity   1717 F.... timidity

willard@naglfar: ~
$ screen -dm -S music mplayer Music/Manowar/Battle_Hymns_MMXI/07.Williams_Tale.flac

willard@naglfar: ~
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1112 F.... slmodemd
                     willard    2039 F.... pulseaudio
                     willard    4102 F.... alsamixer
/dev/snd/pcmC0D0p:   willard    2039 F...m pulseaudio
/dev/snd/pcmC0D6c:   Slmodemd   1112 F.... slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1112 F.... slmodemd
/dev/snd/seq:        timidity   1717 F.... timidity
```

---

### Post by lidex on 2011-05-22
Haven't seen this one for awhile. The easiest thing to do is to remove the sl-modem package, that is if you don't use the modem.
```
sudo apt-get remove sl-modem-daemon
```
Reboot.
Reference:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Another%20process%20locking%20the%20sound%20card](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Another%20process%20locking%20the%20sound%20card)

---

### Post by Willard on 2011-05-23
> **lidex said:**
> Haven't seen this one for awhile. The easiest thing to do is to remove the sl-modem package, that is if you don't use the modem.
```
sudo apt-get remove sl-modem-daemon
```
Reboot.
Reference:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Another%20process%20locking%20the%20sound%20card](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Another%20process%20locking%20the%20sound%20card)
@ sl-modem-daemon: That's just hilarious.

I removed the daemon, and rebooted. But the problem persists.

Note that the volume of the "pop" is the same, regardless of what my master volume is (it is, of course, lower if I lower the volume on my speakers...).

UPDATE: I think after I removed sl-modem-daemon that the pop now only occurs when I mute/unmute my master volume. It does not happen now when I, for instance, raise/lower the volume using my laptop hotkeys (unless I mute).

For completeness, in case this does not fix you problem, I will have you know that I also removed timidity.```
willard@naglfar: ~
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for willard: 
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  willard    1986 F.... pulseaudio
```
I can live with the pop only occurring when I mute/unmute my sound. But if you can think of a way to remove it, I would be happier.

---

### Post by sanderd17 on 2011-05-26
I don't have the sl-modem-deamon installed, but I notice that the pop also happens with OpenSuse, just the same symptoms.

---

### Post by lidex on 2011-05-26
@Willard
Can you try this and report results please. Basically adding a modprobe option to disable power save.
```
echo "options snd-hda-intel power_save_controller=N" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

