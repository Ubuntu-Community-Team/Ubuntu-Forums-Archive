---
title: "The Sound doesn't work with my speaker"
date: 2008-05-11
forum: Hardware
---

### Post by Xun on 2008-05-11
Hey !

Firstly, excuse my English, who is so bad ... I'm learning English at school !

Well, I have a big problem, my sound does not work with my speaker. 
It's boring ...

My laptop is a TOSHIBA p100-474 and during the alpha 3 or 4, _sound worked_ _with or without_ speaker.

I'm on ubuntu 8.04, and backports's actived.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
alex@alex-laptop:~$ 

```

Can you help me ?
For more informations, contact me !

Thanks,
Xun

PS: Thank you for me to point out my errors of spelling

---

### Post by ajmorris on 2008-05-11
hi,
could you please run: ```
sudo alsaconf
``` and then after it has finished, run alsamixer

En francais:
salut,
est-ce que tu puet a executer: ```
sudo alsaconf
``` et, ensuite, a executer alsamixer.
Pardonnez les accents :)

Aussi, j'apprends le francais a l'ecole, et je connais le difficulte de apprendre un langue seconde. Si tu voudrais d'aide avec ton anglais... je peut essayer pour t'aider :)

AJ

---

### Post by Xun on 2008-05-11
Hi,

If I do "sudo alsaconf", terminal sends:

```
alex@alex-laptop:~$ sudo alsaconf
sudo: alsaconf: command not found
```

What I do ?

Xun

---

### Post by Xun on 2008-05-11
up ...

What should I do? What has changed between the alpha 3 and alpha 5?

Xun

---

### Post by erginemr on 2008-05-11
This is a really problematic card that gave many Ubunteros head aches in Gutsy:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

(1) Diagnostics: Can you please post the output of the following four diagnostic commands:
[http://ubuntuforums.org/showpost.php?p=4575682&postcount=2](http://ubuntuforums.org/showpost.php?p=4575682&postcount=2)

(2) Possible Solution: This is the next step to do, depending on the output of the above commands:
[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

---

### Post by Xun on 2008-05-12
Hello,

* aplay -l
```

**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : CONEXANT Analog [CONEXANT Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : Conexant Digital [Conexant Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```

* cat /proc/asound/cards
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2400000 irq 22 
```
 * cat /proc/asound/cards
 ```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2400000 irq 22

```

 * cat /proc/asound/card0/codec#* | grep Codec says Codec: Conexant CX20549 (Venice)


Finally, you propose me to see this page: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24).

I downloaded alsa_1.sh, alsa_2.sh and I "chmod 777" on.

I run alsa_1.sh, all is ok and I reboot. I wont run alsa_2.sh, but I have error message: 

```

alex@alex-laptop:~$ cd /home/alex/Download/
alex@alex-laptop:~/Download$ sudo sh ./alsa_2.sh 
`/lib/modules/2.6.24-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
cp: ne peut créer le fichier régulier `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko': Aucun fichier ou dossier de ce type
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-hda-intel.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-hda-intel.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-hwdep.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-hwdep.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-mixer-oss.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-mixer-oss.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-page-alloc.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-page-alloc.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-pcm-oss.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-pcm-oss.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-pcm.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-pcm.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-rtctimer.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-rtctimer.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-device.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-seq-device.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-midi-event.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-seq-midi-event.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq-oss.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-seq-oss.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-seq.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-seq.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd-timer.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd-timer.ko'
`/usr/src/alsa/alsa-driver-1.0.16/modules/snd.ko' -> `/lib/modules/2.6.24-16-generic/kernel/sound/snd.ko'
cp: omission du répertoire `/lib/modules/2.6.24-16-386/kernel/sound/'
alex@alex-laptop:~/Download$ 

```

omission du répertoire = omission of Directory

I don't know what I should do ...

Xun

Edit: I can make an alsaconf, what I did

---

### Post by erginemr on 2008-05-12
Hi Xun / Alex,

You don't have to worry about translations; I can speak French, too.

The thing is, I am at work and cannot peek at the forums' site with the boss on my back ;). I'll write a proper response as soon as I get back home...

---

### Post by erginemr on 2008-05-12
I have checked the contents of the two scripts but could not identify the reason of the failure either. Having no better advice:

(1) Please make sure that you have followed the initial steps (enabling repositories) in here:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)
> Make sure you go to System -> Administration -> Software Sources and have the first 4 repositories enabled (also make sure the CD is disabled unless you have a slow internet and would prefer to use the older versions of the packages on the CD). When you close that dialog, Ubuntu will ask you to update your software sources. Make sure you don't have Update Manager or Synaptic Package Manager open and click yes/ok to update the package list.

(2) Please check that you have all pre-requisites installed:
```
dpkg -l build-essential gettext linux-headers-`uname -r`
```
All three packages should report "ii", meaning "installed".

(3) Try to re-run the scripts, paying special attention to whether the first one runs without any error message. In any case, you can check your ALSA version with:
```
alsactl -v
```

(4) Failing that, and following this aforementioned guide:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
you may still try adding a line to your "/etc/modprobe.d/alsa-base" file with:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add the following line to the end of the file:
```
options snd-hda-intel model=toshiba
```
Reboot each time, replacing **toshiba** with **auto** first, and then with **laptop**, and with **3stack**, until you get to hear the sound.

(5) And there is also always a possibility that your sound volume is just turned off. So, please also rule out that possibility by checking all volume levels from:
a. ```
alsamixer
```
b. Double-click Gnome volume icon -> Menu -> Change Device
c. Main Menu -> System -> Preferences -> Sound: Play with settings

---

### Post by Xun on 2008-05-13
Hi,

Thanks for your quickly reply !

dpkg -l build-essential gettext linux-headers-`uname -r`
```


Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nom            Version        Description
+++-==============-==============-============================================
ii  build-essentia 11.3ubuntu1    informational list of build-essential packag
ii  gettext        0.17-2ubuntu1  GNU Internationalization utilities
ii  linux-headers- 2.6.24-16.30   Linux kernel headers for version 2.6.24 on x
alex@alex-laptop:~$

```

alsactl -v
```
alsactl version 1.0.16
```

options snd-hda-intel model=XXXX, toshiba, laptop, 3stack are options what I have already tryed ...

alsamixer: all is ok but IEC958 stays of 0 ... I can't change it.

Thanks for your help !

Xun

---

### Post by Xun on 2008-05-15
Hey,

Up :p

Xun

---

### Post by erginemr on 2008-05-15
Which one:

Sound is up -> :D

Or BUMP -> :(

---

### Post by Xun on 2008-05-15
The Sound on my speakers is still down ...

Did the Alsa version change between the Alpha 3 (or 4) and the Final version ?

Xun

---

### Post by Xun on 2008-05-19
Nobody knows ? ...

Xun

---

### Post by Xun on 2008-05-26
Up ...

I have tried to boot with 'acpi=off', but no change, my sound doesn't work by green jack.

Xun

---

