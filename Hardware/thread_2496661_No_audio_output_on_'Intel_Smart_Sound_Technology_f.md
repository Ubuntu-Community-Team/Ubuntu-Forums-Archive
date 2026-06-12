---
title: "No audio output on 'Intel Smart Sound Technology for Bluetooth Audio'"
date: 2024-04-07
forum: Hardware
---

### Post by bdobby on 2024-04-07
Hi.
I've installed Ubuntu 22.04 on my Dell Inspiron and I'm getting no sound. The settings->audio->output_device panel shows 'Dummy Output', so I suspect the required driver is missing or misconfigured. 

The OS is Linux version 6.5.0-26-generic (buildd@lcy02-amd64-051)
The audio system is listed as 'Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller'. 

Can anyone help please?

Thanks
Peace & Love
Brian

---

### Post by #&amp;thj^% on 2024-04-07
Will you include this please:
```
systemctl --user --now status pipewire pipewire-pulse wireplumber

```

I'm not sure I can help you though.

---

### Post by bdobby on 2024-04-07
Hi.
Thanks for your reply. Here's the output. It doesn't mean much to me. In particular, I don't understand the last line. AFAIK I did nothing at 16:24:28 to start a service.

```

Unit pipewire-pulse.service could not be found.
Unit wireplumber.service could not be found.
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-04-07 16:24:28 BST; 4h 26min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1540 (pipewire)
      Tasks: 2 (limit: 18650)
     Memory: 1.6M
        CPU: 40ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1540 /usr/bin/pipewire


Apr 07 16:24:28 megadodo systemd[1533]: Started PipeWire Multimedia Service.
~

```

---

### Post by #&amp;thj^% on 2024-04-07
That's just the system telling you it's running ie:
```
systemctl --user --now status pipewire pipewire-pulse wireplumber
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: enabled)
     Active: active (running) since Sun 2024-04-07 11:55:46 MDT; 2h 12min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1089 (pipewire)
      Tasks: 2 (limit: 16372)
     Memory: 11.9M (peak: 12.9M)
        CPU: 148ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;1089 /usr/bin/pipewire

[B][COLOR="#FF0000"]Apr 07 11:55:46 btrfs-cachy systemd[1077]: Started PipeWire Multimedia Service.
[/COLOR][/B]
&#9679; pipewire-pulse.service - PipeWire PulseAudio
     Loaded: loaded (/usr/lib/systemd/user/pipewire-pulse.service; enabled; preset: enabled)
     Active: active (running) since Sun 2024-04-07 11:55:46 MDT; 2h 12min ago
TriggeredBy: &#9679; pipewire-pulse.socket
   Main PID: 1091 (pipewire-pulse)
      Tasks: 2 (limit: 16372)
     Memory: 15.3M (peak: 15.9M)
        CPU: 559ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire-pulse.service

```
See the red highlighted portion..

Dose this file exist ?
```
ls /etc/modprobe.d/alsa-base.conf

```

---

### Post by bdobby on 2024-04-08
Yes

```

brian@megadodo:~$ cat /etc/modprobe.d/alsa-base.conf 
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

### Post by #&amp;thj^% on 2024-04-08
At the bottom of that file will you add this to it.
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
```
options snd-hda-intel dmic_detect=0
options snd-hda-intel index=0
```
This will most likely break your Mic, just a heads up.
And a reboot to see if this helps with sound.

---

### Post by bdobby on 2024-04-08
No, it didn't help

---

### Post by #&amp;thj^% on 2024-04-08
You can remove those two entries now.

I have no more suggestions for you. :(

---

### Post by bdobby on 2024-04-08
Ok. Thanks for your time.

---

