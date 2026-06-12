---
title: "Audio/ALSA unable to work on Lenovo z580"
date: 2014-12-29
forum: Hardware
---

### Post by linuxmann on 2014-12-29
Hi all,

I have just recently installed 14.04LTS on a z580 laptop. The sound codec does not seem to be recognized. Within the sound settings, it is specified that it is a Dummy Output. I have dug through the lenovo forums to find an answer and it specified that i had to install this:

[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.1/alsa-driver-linuxant_1.0.23.1_all.deb.zip)

I wound up installing this and voila! It works! But, only for a short amount of time. Only when i suspend or shut down the laptop is when it stops working. I also need to mention that the installation errors out but still installs... I have an intel codec onboard if that can help solve my issue.

Selecting previously unselected package alsa-driver-linuxant.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 203275 files and directories currently installed.)
Preparing to unpack .../alsa-driver-linuxant_1.0.23.1_all.deb ...
Unpacking alsa-driver-linuxant (1.0.23.1) ...
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 3.13.0-43-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.8171.log
dpkg: error processing package alsa-driver-linuxant (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead (0.100.0-16) ...


--------------------------------------------------------------------------------------------------------------------------------------------

I open the log for the installation:

rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
echo skipping rm -f alsa-kernel/include/version.h
skipping rm -f alsa-kernel/include/version.h
rm -fr .tmp_versions
rm -f Module.symvers
find include/sound -name "*.h" -type l | xargs rm -f
rm -fr include/generated
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/3.13.0-43-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... no
The file /lib/modules/3.13.0-43-generic/build/include/INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.13.0-43-generic/build).



Anyone that can help, it would be greatly appriciated. If more information is needed, please let me know.

---

### Post by Yellow Pasque on 2014-12-29
Run the command:
```
sudo aupdate-pciids
```

Then, get more detailed info: [https://duckduckgo.com/l/?kh=-1&uddg=https%3A%2F%2Fwiki.ubuntu.com%2FAudio%2FAlsaInfo](https://duckduckgo.com/l/?kh=-1&uddg=https%3A%2F%2Fwiki.ubuntu.com%2FAudio%2FAlsaInfo)

Quick google seems to indicate a Realtek codec on this model, so installing the Conexant/Linuxant driver would be a bad idea.

---

### Post by linuxmann on 2014-12-29
EDIT: Audio device - Intel corporation 7 series/c210 series chipset family high definition audio controller

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Mon Dec 29 16:44:09 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.1 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      IdeaPad Z580    
Product Version:   Lenovo Z580                     
Firmware Version:  5FCN89WW


!!Kernel Information
!!------------------

Kernel release:    3.13.0-43-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.27.2
Utilities version:  1.0.27.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1e20 (rev 04)
	Subsystem: 17aa:3977


!!Modprobe options (Sound related)
!!--------------------------------

snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---- 1 root audio 116,  1 Dec 28 19:44 /dev/snd/seq
crw-rw---- 1 root audio 116, 33 Dec 28 19:44 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ctr
ccm
bnep
rfcomm
bluetooth
arc4
iwldvm
mac80211
uvcvideo
intel_rapl
x86_pkg_temp_thermal
videobuf2_vmalloc
intel_powerclamp
videobuf2_memops
videobuf2_core
rts5139
videodev
coretemp
iwlwifi
kvm
cfg80211
mei_me
mei
lpc_ich
joydev
serio_raw
ideapad_laptop
sparse_keymap
mac_hid
parport_pc
ppdev
lp
parport
xts
gf128mul
dm_crypt
crct10dif_pclmul
i915
crc32_pclmul
ghash_clmulni_intel
cryptd
i2c_algo_bit
drm_kms_helper
drm
ahci
psmouse
r8169
libahci
mii
wmi
video


!!ALSA/HDA dmesg
!!--------------
```

---

### Post by Yellow Pasque on 2014-12-29
If you're going to post a bunch of text, please use code tags. Also, please give **audio** information:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

 (sorry about not posting the correct link in my last post).

---

### Post by linuxmann on 2014-12-29
> **Temüjin said:**
> If you're going to post a bunch of text, please use code tags. Also, please give **audio** information:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

 (sorry about not posting the correct link in my last post).

I made an edit with alsa info.

---

### Post by Yellow Pasque on 2014-12-29
> Driver version:     
Library version:    1.0.27.2
Utilities version:  1.0.27.2

Yeah, it looks like you've borked the kernel modules/drivers/
Try this to get the latest modules installed: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by linuxmann on 2014-12-29
I have attempted the fix but however, still no luck. I've also updated the kernel to the latest stable version. One thing i did notice is that the driver configuration files are not installed. I go about installing them from the software center but i get this. Under the audio settings, it still says "Dummy Output". (Image attached) [IMG]http://i59.tinypic.com/2mm6zwz.png[/IMG]

---

### Post by linuxmann on 2014-12-29
Tried just about everything i could.

Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

It seems like it's not even recognized to begin with. I have everything installed with pulseaudio and alsa that is required and i get the same message on terminal along with the dummy input.

---

