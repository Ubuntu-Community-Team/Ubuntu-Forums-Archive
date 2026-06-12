---
title: "Sound on Compaq Mini 311c 1020SA not working"
date: 2010-08-04
forum: Hardware
---

### Post by AvicusUK on 2010-08-04
Hi, there

I recently installed Ubuntu 9.04 on my Compaq Mini 311C Netbook to find that everything seems to work perfectly except there is no sound coming from the built-in speakers.

I've tried upgrading ALSA to the latest release using SUDO but there are download errors when using WGET.

Is there any other way to get this working?

I would really appreciate help, I'm really desperate. I really don't want to get back to Windows.

Thanks in advance

Miguel

---

### Post by utilitytrack on 2010-08-04
> I really don't want to get back to Windows.

Hello, I hope you will don't need this :)
Please say why you need use [FONT=Courier New]wget[/FONT]? And post here output of these commands:
 ```
$ uname -r

$ dpkg -l alsa-*


$ lspci -nn | grep Audio


$ cat /proc/asound/card0/codec#0 | grep Codec


# hwinfo --sound


$ cat /etc/modprobe.d/alsa-base.conf
```

and your PC/laptop model
also recheck levels in alsamixer

---

### Post by AvicusUK on 2010-08-04
I followed intructions from a forum to upgrade to ALSA 2.0.23

My current version is 2.0.18 which cause issues with my netbook model

---

### Post by utilitytrack on 2010-08-04
1) you make mistake with ALSA version

2) see my previous post

---

### Post by AvicusUK on 2010-08-04
right the results are

**$ uname -r**
2.6.28-19-generic

**$ dpkg -l alsa-***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.18.dfsg-1u ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-utils     1.0.18-1ubuntu ALSA utilities
[B]
$ lspci -nn | grep Audio[/B]
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)

**$ cat /proc/asound/card0/codec#0 | grep Codec**
Codec: IDT 92HD81B1X5

**$ hwinfo --sound**
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
bash: hwinfo: command not found

**$ cat /etc/modprobe.d/alsa-base.conf**
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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

---

### Post by AvicusUK on 2010-08-04
I've installed HWINFO and used the command. This the result 

**$ hwinfo --sound**
15: PCI 08.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_10de_ac0
  Unique ID: RE4e.d3TDkwQDB4B
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: sound
  Model: "nVidia Audio device"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0ac0 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3651 
  Revision: 0xb1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x53100000-0x53103fff (rw,non-prefetchable)
  IRQ: 21 (3962 events)
  Module Alias: "pci:v000010DEd00000AC0sv0000103Csd00003651bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

### Post by utilitytrack on 2010-08-04
Hello again, I saw this
> [FONT=Courier New]alsa-base 1.0.18.dfsg-1u ALSA driver configuration files[/FONT]

that's bad, because many changes have been made in IDT 92HD8xx codecs family since v1.0.18. So I advice you upgrade your ALSA to last stable version (1.0.23). Follow [[COLOR=#0000FF]these instructions[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") and give your impressions here. Good luck!

---

### Post by AvicusUK on 2010-08-04
my problem got sorted with the alsa update script in this thread

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

but many thanks for your help

:)

---

### Post by utilitytrack on 2010-08-04
I very glad for you. Please mark this thread as solved.

---

