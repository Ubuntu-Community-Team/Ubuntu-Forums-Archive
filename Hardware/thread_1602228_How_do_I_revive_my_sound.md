---
title: "How do I revive my sound?"
date: 2010-10-21
forum: Hardware
---

### Post by dining_philosopher on 2010-10-21
Hello!

I tried to output sound via hdmi. Most search results claim that installing alsa 1.0.23 addresses the issue. I copypasted commands from [http://translate.google.ru/translate?js=n&prev=_t&hl=ru&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http://help.ubuntu.ru/wiki/alsa&act=url](http://translate.google.ru/translate?js=n&prev=_t&hl=ru&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http://help.ubuntu.ru/wiki/alsa&act=url) , but sound disappeared at all. I uninstalled pulseaudio as recommended in the same wiki with the same effect. Uninstallation and reinstallation of alsa and some other packages also gave no result.

```
wormball@wormball-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid
wormball@wormball-desktop:~$ uname -a
Linux wormball-desktop 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
wormball@wormball-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.3 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

I have virtually no idea what to do.

Thanks in advance.

---

### Post by awechris on 2010-10-21
the same problem happened to me when I tried compiling and installing a daily build of alsa. I uninstalled it, reinstalled... the problem is still there.

---

### Post by na5h on 2010-10-21
Not sure if this will help, but...back when I had problems with my sound I used "sudo alsa force-reload" to get it working. Then I used typed "alsamixer" and put all the volume-levels up. Not sure if it will do any good in this case! :confused:

---

### Post by dining_philosopher on 2010-10-21
```
wormball@wormball-desktop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/wormball/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/wormball/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
```

With 2.6.32 kernel sound is played via front audio jack and one of rear jacks, but other than it did before.

---

### Post by dining_philosopher on 2010-10-22
If i upgrade to maverick, will it solve my problem?

---

### Post by dining_philosopher on 2010-10-24
?

---

### Post by dining_philosopher on 2010-10-25
Hello again!

I followed instructions in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , and when i entered command

sudo module-assistant a-i   alsa-source

, it said that it can't find header files and i should install linux-headers-2.6.34-020634-generic. But aptitude says that this package is already installed, and reinstalling it has no effect.

Then i followed alternative pathway which, in turn, requires

 cd /usr/src sudo tar xjvf alsa-driver.tar.bz2 cd modules/alsa-driver

. I suspect that there is erratum in the article and actually there should be three commands


 cd /usr/src
 sudo tar xjvf alsa-driver.tar.bz2
 cd modules/alsa-driver

, so i entered them, and entered configure command which says

wormball@wormball-desktop:/usr/src/modules/alsa-driver$ sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/modules/alsa-driver
checking cross compile... 
checking for directory with ALSA kernel sources... ./configure: line 4715: cd: ../alsa-kmirror: No such file or directory
../alsa-kmirror
checking for directory with kernel source... /usr/src/linux-headers-2.6.34-020634-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... no
The file /usr/src/linux-headers-2.6.34-020634-generic/include/linux/autoconf.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.34-020634-generic/build).

, so it also cannot find headers and, moreover, cannot find alsa-kmirror.

Where is the root of all evil and what should i do?

---

### Post by lidex on 2010-10-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by dining_philosopher on 2010-10-26
[http://www.alsa-project.org/db/?f=7c79d83eb08ea2e1b451a4781098246a6b4b086e](http://www.alsa-project.org/db/?f=7c79d83eb08ea2e1b451a4781098246a6b4b086e)

> 
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Tue Oct 26 18:25:31 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      P55M-UD2


!!Kernel Information
!!------------------

Kernel release:    2.6.34-020634-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3b56 (rev 06)
	Subsystem: 1458:a002
--
01:00.1 0403: 10de:0be4 (rev a1)
	Subsystem: 1462:2072


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
btrfs
zlib_deflate
crc32c
libcrc32c
ufs
qnx4
hfsplus
hfs
minix
ntfs
vfat
msdos
fat
jfs
xfs
exportfs
reiserfs
binfmt_misc
ppdev
vboxnetadp
vboxnetflt
vboxdrv
arc4
b43
mac80211
it87
hwmon_vid
cfg80211
joydev
led_class
serio_raw
nvidia
intel_agp
soundcore
lp
parport
usbhid
hid
usb_storage
ohci1394
pata_jmicron
floppy
ieee1394
ssb
ahci
r8169
mii


!!ALSA/HDA dmesg
!!------------------




---

### Post by lidex on 2010-10-26
The outcome of all this is that alsa is not correctly installed. I suggest doing this to get back to a default install. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
Now please run the alsa-info script again.

---

### Post by dining_philosopher on 2010-10-27
[http://www.alsa-project.org/db/?f=099a7eadfa438e668bfec6e94388a1e905c50618](http://www.alsa-project.org/db/?f=099a7eadfa438e668bfec6e94388a1e905c50618)

There is still no sound output but some quiet sounds like dialup modem appeared in the front audio jack.

---

### Post by lidex on 2010-10-27
> **dining_philosopher said:**
> [http://www.alsa-project.org/db/?f=099a7eadfa438e668bfec6e94388a1e905c50618](http://www.alsa-project.org/db/?f=099a7eadfa438e668bfec6e94388a1e905c50618)

There is still no sound output but some quiet sounds like dialup modem appeared in the front audio jack.

You'll likely need latest version of alsa for this to work.
Use the alsa-upgrade link in my sig.

---

### Post by dining_philosopher on 2010-10-28
sudo ./AlsaUpgrade-1.0.23-2.sh -c works for several minutes and then says:

> Making all in a52
make[2]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23/a52'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -I/usr/include/alsa   -I/usr/local/include -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF ".deps/pcm_a52.Tpo" -c -o pcm_a52.lo pcm_a52.c; \
	then mv -f ".deps/pcm_a52.Tpo" ".deps/pcm_a52.Plo"; else rm -f ".deps/pcm_a52.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -Wall -g -I/usr/include/alsa -I/usr/local/include "-DAVCODEC_HEADER=<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF .deps/pcm_a52.Tpo -c pcm_a52.c  -fPIC -DPIC -o .libs/pcm_a52.o
/bin/bash ../libtool --tag=CC --mode=link gcc -Wall -g -I/usr/include/alsa   -I/usr/local/include -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -module -avoid-version -export-dynamic -no-undefined   -o libasound_module_pcm_a52.la -rpath /usr/lib/alsa-lib  pcm_a52.lo -lasound   -pthread -L/usr/local/lib -lavcodec -ldl -lasound -lm -lavcore -lavutil   -lasound 
gcc -shared  .libs/pcm_a52.o  -L/usr/local/lib -lavcodec -ldl -lm -lavcore -lavutil /usr/lib/libasound.so  -pthread -Wl,-soname -Wl,libasound_module_pcm_a52.so -o .libs/libasound_module_pcm_a52.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `a64multi_encoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23/a52'
make[1]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2

***************************************************************************
*  alsa-plugins-1.0.23 make failed
***************************************************************************
wormball@wormball-desktop:~/****$

---

### Post by mastablasta on 2010-10-28
Try following this how to then:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

should work just fine.

Only issue i had sometimes second package iddn't want to download and i had to repeat the command to reinstall it.

---

### Post by dining_philosopher on 2010-10-28
I didn't follow advices in mastablasta's link yet.

I STFW'd and found advices to enter

 export CFLAGS="-fPIC"
 export CXXFLAGS="-fPIC"

before compilation, but it didn't help. Despite this, i entered


sudo ./AlsaUpgrade-1.0.23-2.sh -i
sudo reboot

and rhythmbox also didn't play sound after reboot. But after a while i clicked some video (flash/chrome) and heard sound from my headphones connected to front jack!! Summary of sound playing capabilities:

- rhythmbox
+ chrome/flash
+ chrome/html5
+ firefox/flash
- skype
- vlc
+ smplayer
+ mythtv
- totem (doesn't play video at all)
- dragon (doesn't play video at all)

Sound is played from center bottom rear jack, whereas before it was played from the left upper rear jack.

How do i make all programs from the list play sound?

---

### Post by lidex on 2010-10-28
> **dining_philosopher said:**
> I didn't follow advices in mastablasta's link yet.

I STFW'd and found advices to enter

 export CFLAGS="-fPIC"
 export CXXFLAGS="-fPIC"

before compilation, but it didn't help. Despite this, i entered


sudo ./AlsaUpgrade-1.0.23-2.sh -i
sudo reboot

and rhythmbox also didn't play sound after reboot. But after a while i clicked some video (flash/chrome) and heard sound from my headphones connected to front jack!! Summary of sound playing capabilities:

- rhythmbox
+ chrome/flash
+ chrome/html5
+ firefox/flash
- skype
- vlc
+ smplayer
+ mythtv
- totem (doesn't play video at all)
- dragon (doesn't play video at all)

Sound is played from center bottom rear jack, whereas before it was played from the left upper rear jack.

How do i make all programs from the list play sound?
Can you run alsa-info script again please?

---

### Post by dining_philosopher on 2010-10-29
[http://www.alsa-project.org/db/?f=111ac01ca158a76a9356e4879e415c3ce947f5f9](http://www.alsa-project.org/db/?f=111ac01ca158a76a9356e4879e415c3ce947f5f9)

---

### Post by dining_philosopher on 2010-10-31
?

---

### Post by lidex on 2010-10-31
> **dining_philosopher said:**
> ?

Are you using a custom kernel install? If you have a 2.6.32* kernel, try booting into that and see what happens.

---

### Post by dining_philosopher on 2010-11-02
Oh no!1 The sound disappeared at all again! I use 2.6.34 from kernel.ubuntu.com.

---

### Post by dining_philosopher on 2010-11-02
With 2.6.32 situation is the same

> - rhythmbox
+ chrome/flash
+ chrome/html5
+ firefox/flash
- skype
- vlc
+ smplayer
+ mythtv
- totem (doesn't play video at all)
- dragon (doesn't play video at all)


Alsa-info under 2.6.32 [http://www.alsa-project.org/db/?f=45c09d0915a4f134ff51dadbc55cbcaa2e4f4f0c](http://www.alsa-project.org/db/?f=45c09d0915a4f134ff51dadbc55cbcaa2e4f4f0c)

---

### Post by lidex on 2010-11-02
> **dining_philosopher said:**
> With 2.6.32 situation is the same



Alsa-info under 2.6.32 [http://www.alsa-project.org/db/?f=45c09d0915a4f134ff51dadbc55cbcaa2e4f4f0c](http://www.alsa-project.org/db/?f=45c09d0915a4f134ff51dadbc55cbcaa2e4f4f0c)

Still in 2.6.32 use the link in my sig to update to full 1.0.23 alsa. But first make sure these are installed:
```
sudo aptitude install build-essential libncurses5-dev
```

---

### Post by dining_philosopher on 2010-11-04
Still the same in 2.6.32

> Making all in a52
make[2]: &#1042;&#1093;&#1086;&#1076; &#1074; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23/a52'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -Wall -g -I/usr/include/alsa   -I/usr/local/include -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF ".deps/pcm_a52.Tpo" -c -o pcm_a52.lo pcm_a52.c; \
	then mv -f ".deps/pcm_a52.Tpo" ".deps/pcm_a52.Plo"; else rm -f ".deps/pcm_a52.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -Wall -g -I/usr/include/alsa -I/usr/local/include "-DAVCODEC_HEADER=<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF .deps/pcm_a52.Tpo -c pcm_a52.c  -fPIC -DPIC -o .libs/pcm_a52.o
/bin/bash ../libtool --tag=CC --mode=link gcc -Wall -g -I/usr/include/alsa   -I/usr/local/include -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -module -avoid-version -export-dynamic -no-undefined   -o libasound_module_pcm_a52.la -rpath /usr/lib/alsa-lib  pcm_a52.lo -lasound   -pthread -L/usr/local/lib -lavcodec -ldl -lasound -lm -lavcore -lavutil   -lasound 
gcc -shared  .libs/pcm_a52.o  -L/usr/local/lib -lavcodec -ldl -lm -lavcore -lavutil /usr/lib/libasound.so  -pthread -Wl,-soname -Wl,libasound_module_pcm_a52.so -o .libs/libasound_module_pcm_a52.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `a64multi_encoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound_module_pcm_a52.la] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[2]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23/a52'
make[1]: *** [all-recursive] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make[1]: &#1042;&#1099;&#1093;&#1086;&#1076; &#1080;&#1079; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072; `/usr/src/Alsa-1.0.23/alsa-plugins-1.0.23'
make: *** [all] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2


---

### Post by dining_philosopher on 2010-11-07
I compiled alsa [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , but nothing changed.

---

### Post by lidex on 2010-11-07
That's a pretty old guide. What is your alsa info now?

---

### Post by dining_philosopher on 2010-11-08
[http://www.alsa-project.org/db/?f=f59b367f2cf33c09daa16a8fd8e8b96bd33ce1d9](http://www.alsa-project.org/db/?f=f59b367f2cf33c09daa16a8fd8e8b96bd33ce1d9)

---

### Post by lidex on 2010-11-10
Please file a bug report. You can start here. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by dining_philosopher on 2010-12-13
Hello again.

> **lidex said:**
> Please file a bug report. You can start here. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.
This command unfortunately didn't stop its execution.

I upgraded to maverick, and sound disappeared at all.

Some time later on russian forum [http://forum.ubuntu.ru/index.php?topic=125290.msg952459#msg952459](http://forum.ubuntu.ru/index.php?topic=125290.msg952459#msg952459) i was advised to clean ppas and use paman and gstreamer-properties. I turned off [http://ppa.launchpad.net/dtl131/ppa/ubuntu/](http://ppa.launchpad.net/dtl131/ppa/ubuntu/) , udgraded, rebooted, and played with paman, gstreamer-properties and ubuntu sound properties for some time, and suddenly sound has appeared in analog jacks.

But i still wanted to get my sound via hdmi. In order to do so i searched the web and discovered [http://ubuntuforums.org/showthread.php?t=1598489](http://ubuntuforums.org/showthread.php?t=1598489) and therefore [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240) and [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut) . I did

> Using `alsamixer', select your nVidia card (select it from the F6 menu, or use the -c option) and unmute the S/PDIF output (press "m"; the box should change from "MM" to "OO".)

, and it enabled me to hear sine wave from gstreamer-properties hdmi test. Then i acquired list of alsa devices

> $ aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
[/etc/pulse/client.conf:36] Unknown lvalue 'auto-connect-localhost' in section 'n/a'.
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC887 Analog [ALC887 Analog]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: Intel [HDA Intel], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC887 Digital [ALC887 Digital]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: NVIDIA HDMI [NVIDIA HDMI]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 7: NVIDIA HDMI [NVIDIA HDMI]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 0/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 8: NVIDIA HDMI [NVIDIA HDMI]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: NVidia [HDA NVidia], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 9: NVIDIA HDMI [NVIDIA HDMI]
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
 *&#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0


and started to test various players (aplay, mplayer, smplayer, vlc) with explicit designation of output device. Such test revealed that devices 1.3, 1.7, 1.8 and 1.9 are all capable of transmitting sound via hdmi, but do so with some probability, namely 1.7 is more likely and 1.3 is less likely to play sound successfully. As i understood, one device may be used only by one program, and 1.3 is used by pulseaudio. I spent about an hour in such testing, and in millionth time changed output device in ubuntu sound properties, and heard rhythmbox output from my tv speakers. It happened as suddenly as in previous case with analog output, and i also couldn't get which of my actions played crucial role in this.

But in few minutes i heard crackling sounds in loud places of sound files. Moreover, setting digital volume control to value other than 100% led to total replacement of sound output with loud crackling. However, players with manual device designation still played sound clearly, so i concluded that pulseaudio is the root of this evil.

I rebooted, and after reboot i only got the sound from 1.7 and no hdmi sound from rhythmbox or chrome. I suspect that i have to change something in pulseaudio settings, but i don't know what exactly.

Alsa info for now (with new alsa-info.sh) [http://www.alsa-project.org/db/?f=4cd5748f45e298a56f36a019a608cffc00c89564](http://www.alsa-project.org/db/?f=4cd5748f45e298a56f36a019a608cffc00c89564)

---

### Post by dining_philosopher on 2010-12-13
Bingo! I added

load-module module-alsa-sink device=hw:1,7

to /etc/pulse/default.pa (in place with commented similar lines) and did pulseaudio -k. And after that another hdmi appeared in ubuntu sound properties, and activating it took the desired effect.

I do not want to mark this topic as solved 'til next reboot.

---

### Post by dining_philosopher on 2010-12-13
Unfortinately i was right. Whereas rhythmbox acts perfectly, all my video players use much processor time and hang several times per second. Smplayer once reported aborting mplayer with following output:

> 
.........


(many same errors)


.........

AO: [pulse] pa_stream_write() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated

AO: [pulse] pa_stream_write() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated

AO: [pulse] pa_stream_write() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated

AO: [pulse] pa_stream_flush() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated
AO: [pulse] pa_stream_get_latency() failed: Connection terminated


MPlayer interrupted by signal 11 in module: decode_audio
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


---

