---
title: "No sound through speakers. Only headphones."
date: 2009-06-24
forum: Hardware
---

### Post by _BigWings_ on 2009-06-24
Hey all,

Ever since upgrading to 9.04 I haven't been able to get sound through my speakers, I can only get sound through the headphones.

I see that other people have similar problems and I tried to follow the steps to fix it but haven't been able to get the sound back.

The most common reply to this problem is found here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

You are supposed to look what chip and codec you have and then match that with whats in a documentation file but I can't find what I should use and its just all very confusing.

Some information:
my computer is an HP HDX 18 laptop

```

cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD71B7X
Codec: Generic 10de ID 6

```

contents of /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=laptop
```
I noticed that different solution pages talk about different files, some talk about alsa-base, others alsa-base.conf, yet other ones about etc/modprobe.conf
so which file is it?


```
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux martijn-laptop 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xdd000000 irq 22

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG
```

```
lsmod | grep snd
snd_hda_intel         434100  5 
snd_pcm                82948  2 snd_hda_intel
snd_timer              29704  1 snd_pcm
snd                    62628  12 snd_hda_intel,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9600M GT [10de:0649] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technologies, Inc. IEEE 1394 Host Controller [197b:2380]
06:00.1 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
06:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
06:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
06:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
```

I have been wrestling with this problem for too long now and it is the one reason im still using vista. Can someone please help me with this?

---

### Post by philcamlin on 2009-06-24
plug your speaker jack into the headphone hack ?

just an idea... :D :popcorn:

---

### Post by _BigWings_ on 2009-06-27
myeah thats not really the kind of solution i was looking for. Surely it must be just a setting in a file somewhere. Anyone?

---

### Post by Ayuthia on 2009-06-27
You might try this [link]("http://ubuntuforums.org/showpost.php?p=6068909&postcount=26").

---

### Post by _BigWings_ on 2009-06-28
I added the line to the end of my alsa-base file, restarted, and still have no sound :(

can someone with an HDX laptop and working sound post me their alsa-base file?

Mine looks like this now:
```
options snd-hda-intel model=laptop
options snd-hda-intel enable_msi=1
```

their is also another file in the folder, called alsa-base.conf which looks like this:
```
options snd-hda-intel model=hp-m4
```

and another file alsa-base.config
```
options snd-hda-intel position_fix=1 model=3stack
```

maybe its time for a clean. Apart from a complete os reinstall, what is the best way to reinstall the sound system completely?

M

---

### Post by Ayuthia on 2009-06-28
You should be using alsa-base.conf in Jaunty.  I am not for sure if the alsa-base file will be read if the alsa-base.conf file exists.  I am pretty sure that the .config file is not going to work.  It would be best to configure the .conf version and move the other two into your home directory.

---

### Post by JIMIneitor on 2009-06-28
```
$ alsamixer
```

then highlight "front" and turn on the volume, that worked for me when that happened
:lolflag:

---

### Post by _BigWings_ on 2009-06-28
Hmmm I reinstalled the entire os and added the line to the end of alsa-base.conf and restarted: still no sound through the speakers :(

Is there anything else I can try?

---

### Post by JIMIneitor on 2009-06-29
> **JIMIneitor said:**
> ```
$ alsamixer
```then highlight "front" and turn on the volume, that worked for me when that happened
:lolflag:

did you try that?

i swore it worked! :KS

---

### Post by cucisan on 2009-06-29
hi
i also have an HDX18.. i played around with the first jaunty kernel.. it did work with setting to hplaptop or dell-m4 or something.. but sound segfaulted sometimes.. 
i manually patched my kernel with some code from a launchpad post.. but that was not complete..
do yourself some good and just install kernel 2.6.30 from ubuntu kernel ppa..

all sound problems are gone whoohooo ;)

(and start using the nvidia drivers from the nvidia site.. )

just my 2 cents ..

---

### Post by _BigWings_ on 2009-06-29
JIMIneitor:
I checked the mixer and all the channels are unmuted and set to max

cucisan:
how do I install a different kernel?

---

### Post by cucisan on 2009-06-30
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/)

download and install in this order:

linux-headers-2.6.30-020630_2.6.30-020630_all.deb
linux-headers-2.6.30-020630-generic_2.6.30-020630_amd64.deb
linux-image-2.6.30-020630-generic_2.6.30-020630_amd64.deb

or i386 if you installed 32bit ubuntu (then shame on you! why would anyone want to use 32bit versions on 64bit hardware ;))

installing the nvidia driver from nvidia.com also wont be a bad idea...

the only hassle you will ran into.. these kernels are build with gcc-4.2 (don't ask me why..) and ubuntu jaunty default is gcc-4.3...  so nvidia kernel drivers will always fail.. the ubuntu one and the one from the nvidia site...

just install gcc-4.2

go to /usr/bin -> rm gcc (its only symbolic link to gcc-4.3) and then set the link to gcc-4.2 with ln -s gcc-4.2 gcc
afterwards you can revert back to gcc-4.3 using the same procedure..

then nvidia driver will build correctly..


its really easy..

---

### Post by hcollier on 2009-06-30
I have no speakers, only headphones plugged into the sound card. Machine is a Dell desktop with dual Ubuntu 9.0.4 or Windows XP boot. Lots of sound through the headphones with Windows. Dead silence with Ubuntu. I guess I'll just have to wait until Canonical issues a bug fix.

---

### Post by stragulus on 2009-07-01
I too was having this problem with my Fujitsu-Siemens Li-3910 laptop. Today I upgraded to a 2.6.31 kernel and this seems to have solved the sound issue. It seems to screw up my xterm contents though, so it might not be very useable after all.

I got this kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1-fix1/linux-headers-2.6.31-020631rc1gc0d1117-generic_2.6.31-020631rc1gc0d1117_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1-fix1/linux-headers-2.6.31-020631rc1gc0d1117-generic_2.6.31-020631rc1gc0d1117_i386.deb)

---

### Post by _BigWings_ on 2009-07-01
cucisan:

Thanks man, I installed the kernel you suggested and it works!

M

---

### Post by trivial on 2009-07-13
cucisan's fix worked for me.  WUBI install on Vista had no sound, but now it does.

Now, I can *really* get rid of Vista, for good.

Thank you, thank you, thank you.

---

### Post by iamkrazee on 2009-07-15
I had this same problem, so I decided to download a latest kernel, downloaded 31rc3

uname -r output:
```

2.6.31-020631rc3-generic

```

The sound fix worked but now my display is screwed up. I downloaded the latest ATI drivers and installed em. At the boot time, it says DKMS auto installation something something, waits for a few seconds and then says "FAIL". It still does boot me into the system, but only to mess up the display. Line-by-line scrolling gone ultra slow, and no effects for KDE etc. Can anyone please help?

(using kubuntu, but I do have ubuntu-desktop installed)

---

### Post by bucks on 2011-01-23
> **JIMIneitor said:**
> did you try that?

i swore it worked! :KS
Wow, this actually worked for me. I thought I was going to have to use my external speakers forever. THANK YOU!!!

---

