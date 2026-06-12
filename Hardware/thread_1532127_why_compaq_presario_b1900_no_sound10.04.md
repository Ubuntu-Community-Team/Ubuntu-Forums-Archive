---
title: "why compaq presario b1900 no sound?10.04"
date: 2010-07-16
forum: Hardware
---

### Post by leedorian on 2010-07-16
why compaq presario b1900 no sound?
I'v installed the ubuntu 10.04 on my notebook compaq presario b1900,but just no sound.


my alsa-base.conf

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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```


anybody know why?

---

### Post by smardi on 2010-07-16
Pls see if this helps

[http://swiss.ubuntuforums.org/showthread.php?t=1179999&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1179999&page=2)

I also faced same problem..It got resolved following one of these threads and I am not able to trace the particular solution. Do some search and you will get it.

Thanks

---

### Post by leedorian on 2010-07-16
> **robinbilliards said:**
> I've managed to get some sound from headphones plugged into the mic socket.
 I added the following to /etc/modprobe.d/alsa-base.conf:
 options snd-hda-intel model=test
options snd-hda-intel enable_msi=1
 After setting model as "test" and rebooting, the mixer showed many new controls, although most seem to have no effect.
doesn't work.....

---

### Post by leedorian on 2010-07-16
i'v tried many solutions,include upgrade alsa driver,install realteak new driver,modify the alsa-base.conf
doesn't work at all.

---

### Post by smardi on 2010-07-16
[http://ubuntuforums.org/showthread.php?t=1179999&highlight=Compaq+CQ+speaker+sound](http://ubuntuforums.org/showthread.php?t=1179999&highlight=Compaq+CQ+speaker+sound)

this worked for me, do it at your own risk.

Thanks,

---

### Post by leedorian on 2010-07-16
> **smardi said:**
> [http://ubuntuforums.org/showthread.php?t=1179999&highlight=Compaq+CQ+speaker+sound](http://ubuntuforums.org/showthread.php?t=1179999&highlight=Compaq+CQ+speaker+sound)

this worked for me, do it at your own risk.

Thanks,
I added those lines in my alsa-base.conf

```

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1 			 		

```

and my alsa driver version is 1.0.23 for kernel 2.6.32-23-generic (smp)

but, still not working,thanks for your reply.

---

### Post by leedorian on 2010-07-16
the output of aplay -l
> 
card 0: SB [HDA ATI SB], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by smardi on 2010-07-16
I may have something, but you may have to wait, as I do not have Ubuntu system with me now. I will provide something to you by tomorrow...hope it works before that :)

---

### Post by smardi on 2010-07-16
> **smardi said:**
> I may have something, but you may have to wait, as I do not have Ubuntu system with me now. I will provide something to you by tomorrow...hope it works before that :)


try this

Enable backports repository and install

sudo apt-get install linux-backports-modules-alsa-lucid-generic

---

### Post by leedorian on 2010-07-24
> **smardi said:**
> try this

Enable backports repository and install

sudo apt-get install linux-backports-modules-alsa-lucid-generic



still doesn't work

and I try the alsa shell,this is the output:
[http://www.alsa-project.org/db/?f=224f23ac080646432bde68e1d58e4633157b83d8](http://www.alsa-project.org/db/?f=224f23ac080646432bde68e1d58e4633157b83d8)

---

