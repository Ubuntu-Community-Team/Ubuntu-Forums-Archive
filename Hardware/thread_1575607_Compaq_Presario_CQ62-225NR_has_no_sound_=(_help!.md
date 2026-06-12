---
title: "Compaq Presario CQ62-225NR has no sound =( help!"
date: 2010-09-16
forum: Hardware
---

### Post by Niiza on 2010-09-16
I just bought a Compaq Presario CQ62-225NR and am running Ubuntu 10.04 Lynx on it! I love Ubuntu and run it on all my computers but this new laptop doesnt have any sound! the headphone jack outputs sound just fine, but not the laptop speakers.

Any help?

Thanks.

---

### Post by lidex on 2010-09-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"

---

### Post by Niiza on 2010-09-19
sorry it took so long to get back, ive been really busy. here is the output

blue@blue-laptop:~$ uname -a
Linux blue-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
blue@blue-laptop:~$ aplay -1
aplay: invalid option -- '1'
Try `aplay --help' for more information.
blue@blue-laptop:~$ dpkg -1 | grep "alsa"
dpkg: unknown option -1

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
blue@blue-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ID 270
blue@blue-laptop:~$ ^C
blue@blue-laptop:~$

---

### Post by lidex on 2010-09-19
> **Niiza said:**
> sorry it took so long to get back, ive been really busy. here is the output

blue@blue-laptop:~$ uname -a
Linux blue-laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
blue@blue-laptop:~$ aplay -1
aplay: invalid option -- '1'
Try `aplay --help' for more information.
blue@blue-laptop:~$ dpkg -1 | grep "alsa"
dpkg: unknown option -1

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
blue@blue-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ID 270
blue@blue-laptop:~$ ^C
blue@blue-laptop:~$

Those commands are using a lower case L, not the digit 1. Try again please - I find it easier to copy and paste to avoid syntax errors.
```
aplay -l
dpkg -l | grep "alsa"
```

---

### Post by Isola100919 on 2010-09-19
> **lidex said:**
> Those commands are using a lower case L, not the digit 1. Try again please - I find it easier to copy and paste to avoid syntax errors.
```
aplay -l
dpkg -l | grep "alsa"
```

I have the very same laptop with the same problem. This is the output of the above commands:

```
lene@lene-laptop ~ $ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: HDA Generic [HDA Generic]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: HDMI [HDA ATI HDMI], enhet 3: ATI HDMI [ATI HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
lene@lene-laptop ~ $ dpkg -l | grep "ALSA"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  libasound2                            1.0.22-0ubuntu7                                 shared library for ALSA applications
ii  libsdl1.2debian-alsa                  1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA options)
ii  linux-sound-base                      1.0.22.1+dfsg-0ubuntu3                          base package for ALSA and OSS sound systems
lene@lene-laptop ~ $ 
```

EDIT: I do have sound if I plug in external speakers/headphones. No sound on the internal laptop speakers though.

---

### Post by edhysulistyarso on 2010-09-22
so what the solutions?i have the same problem with my laptop...thanks

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by cbarnardo on 2010-10-23
Same problem here. No sound from the builtin speakers. Headphone jack works fine. If I boot into Windows and then back to Lucid the sound works fine. I'm at a loss at what it could be there must be some toggle to turn the builtin speakers on in Ubuntu.

---

### Post by cbarnardo on 2010-10-23
This fixes it [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

