---
title: "deleted home directory"
date: 2006-05-20
forum: Hardware &amp; Laptops
---

### Post by cneil on 2006-05-20
My ALSA sound card stopped working in dapper gnome on a Gateway 7510GX computer.

The interesting thing is that when Ubuntu boots up and there is no problem, I even get to hear the drum sounds that it makes when it asks for my user name.  However, after I am in gnome nothing works at all.  No mp3, not mame sound, and when I play avi files the video works without the sound.  

I have two reasons why this might have happened:

I made a pretty big newbie error.  I deleted the partition that my home directory was on, but everything else in my installation was safe.  I have not backed this partition up, but my installation is fairly new and I didn't have anything important on there.

When I go to Preferences>Sounds there are no sound cards listed.


The second thing is that I installed some new codecs on the same day that I deleted my drive.

I'll include some messages to see if that helps
[email]chartley@UBUNTU:~/.gnom[/email]e2/sound/events$ cat /proc/asound/cards
0 [IXP            ]: ATIIXP - ATI IXP
                     ATI IXP rev 2 with unknown codec at 0xc0503400, irq 217
1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                     ATI IXP Modem rev 2 at 0xc0503800, irq 217



gedit /etc/modprobe.d/alsa-base

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

  
thanks for any help

---

### Post by cneil on 2006-05-20
just an update..
Any 3d acceleration that I had stopped working too.  It is not just my soundcard. 
I'm sure that this has something to do with my deletion of the home directory, but I don't know how to fix it.

---

