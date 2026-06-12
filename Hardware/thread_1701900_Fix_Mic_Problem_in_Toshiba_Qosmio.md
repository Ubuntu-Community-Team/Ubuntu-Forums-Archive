---
title: "Fix Mic Problem in Toshiba Qosmio"
date: 2011-03-07
forum: Hardware
---

### Post by Marcelo Ruiz on 2011-03-07
Hi All,

A user from Launchpad (HalfEmptyHero) asked me to write a little tutorial on how to make the mic work in the Toshiba Qosmio X500. 
Sorry there is no such tutorial. I have been having problems with the mic configuration in Lucid, but it is working fine in Maverick (kernel 2.6.35-27-generic AMD64) with a minor tweak. If you have problems with this method, send a message and I will do my best to help you using hdaAnalizer.py (although I am just a regular ubuntu user -> nothing close to an expert).
Open a terminal and type:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

once gedit shows you alsa-base.conf, go to the bottom of the file and be sure the last two lines are like follow:

```
options snd-usb-audio index=-2
options snd-hda-intel model=hp-laptop
```

Just in case, my whole alsa-base.conf file is as follows:

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
[B]options snd-usb-audio index=-2
options snd-hda-intel model=hp-laptop[/B]
```

I hope this helps people with the same problem!:D

Marcelo.

---

### Post by MoGa on 2011-11-07
Thank you! I have been using one version of kernel since it was the only one that enabled the mic with no problems, this fixed it easily with the latest kernel =)

Cheerz

---

### Post by Marcelo Ruiz on 2012-02-20
An update for the X500.
I finally got the internal and the external mics working.
To do so, use the attached script (taken from [http://ubuntuforums.org/showthread.php?t=1681577]("http://ubuntuforums.org/showthread.php?t=1681577")) to install alsa 1.24-2 (I tried alsa 1.25 but it doesn't compile in Maverick).
After you extracted the script and made it executable, you need to run it in the following order to download '-d', compile '-c' and install '-i' alsa:

```

sudo ./AlsaUpgrade-1.0.24-2.sh -d
sudo ./AlsaUpgrade-1.0.24-2.sh -c
sudo ./AlsaUpgrade-1.0.24-2.sh -i

```

Now back again to edit the alsa-base.conf file:

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

Be sure the last line reads as follows (we are not using the workaround hp-laptop anymore!):

```
options snd-hda-intel model=laptop
```

After this, reboot the computer.

Now, to change the input mic (the one next to the webcam) you need to run:

```
alsamixer
```

then select capture (F4) and use the arrow keys <- and -> to select the mic and the space bar to activate it:

Mic F is the built in microphone and Mic B the external one (for the regular headset).

I hope this helps!

---

