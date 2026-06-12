---
title: "Acer Aspire 8920G Realtek High Definition Audio Driver install instructions"
date: 2009-03-19
forum: Hardware
---

### Post by pedja_portugalac on 2009-03-19
Hi all

Since months we are trying to resolve sound problem on Acer Aspire 8920G laptops. It's High Definition Audio, 5.1 Cinematic Surround - Tuba. Other models with the same sound card have same problem. 

Till now, we found only temporary solution witch enable two front speakers but today I found good news for us. Apparantly, Alsa developers together with Realtek has found solution in those latest driver (alsa-driver-1.0.19-5.11) on 2009/3/6. I found this on the Realtek official site. The only problem now is that I don't understand, very well, Ubuntu install and configuration instuctions from Realtek team. So if someone is able to get this 5.1 Surround work, please let us know with the step by step how-to like we do it here. Thanks in advance.

The new Alsa Realtek High Definition Audio Driver package is available here: [http://www.realtek.com.tw/downloads/searchView.aspx?keyword=Linux](http://www.realtek.com.tw/downloads/searchView.aspx?keyword=Linux)

The install and configuration instructions I don't understand well are:

The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. alsaconf
	f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.

---

### Post by pedja_portugalac on 2009-03-19
Ok guys, after extracting LinuxPkg_5.11 and changed to that directory I didn't fallow Ubuntu instructions and run install script like this:
> $ sudo ./install
After that I rebooted ones and then run fallowing instruction on screen:
> $ sudo alsaconf
Then:
> $ alsamixer
And I put all first 5 columns to maximum level.

Then I downloaded 5.1 Surround Test File from: [http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3](http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3)

And all 5 speakers worked. I don't know if the TUBA technology worked as well but you can trust me it was well strong volume. Played in Totem and in svn Mplayer. I could clearly hear all 5 speaker one at the time. :lol:

Hope this can be useful for the others. :lol:

---

### Post by pedja_portugalac on 2009-04-14
Today I installed daily image of jaunty 9.04 and still no sound out of the box. After adding this two lines to /etc/modprobe.d/alsa-base.conf 

> #added by myself
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

unmuting all chanels in 

> gnome-volume-control

and putting all them to the maximum level in

> alsamixer

5.1 Surround work after reboot. ;)

PS. Maybe you should also edit /etc/pulse/daemon.conf

> In the terminal, type the following:

sudo gedit /etc/pulse/daemon.conf

This should open up the configuration file in gedit. Once open, scroll down to find the line ; default-sample-channels = 2. Remove the semicolon at the start of the line and change the line according to your surround sound configuration:

      For 2.0 channel sound: default-sample-channels = 2

      For 4.0 channel sound: default-sample-channels = 4

      For 5.0 channel sound: default-sample-channels = 5

* For 5.1 channel sound: default-sample-channels = 6  (this line for acer aspire 8920g)

      For 7.1 channel sound: default-sample-channels = 8 

Save the file the restart your computer. 

You can download test files from:

[ftp://ling.lll.hawaii.edu/pub/greg/gt-demo.tar.gz](ftp://ling.lll.hawaii.edu/pub/greg/gt-demo.tar.gz)

---

### Post by njgriffin on 2009-08-30
Hi there,

Just spent most the evening installing Ubuntu on my 8920g,  Have sound working or at least in part.  My big issue is trying to get the audio over HDMI working, i use mine as a htpc. I can't seem to even get Ubuntu to recognise that there i any audio HDMI capability at all.  Video works fine.

Have you tried hdmi audio at all?

N

---

### Post by pedja_portugalac on 2009-08-30
> **njgriffin said:**
> Hi there,

Just spent most the evening installing Ubuntu on my 8920g,  Have sound working or at least in part.  My big issue is trying to get the audio over HDMI working, i use mine as a htpc. I can't seem to even get Ubuntu to recognise that there i any audio HDMI capability at all.  Video works fine.

Have you tried hdmi audio at all?

N

Audio over HDMI doesn't worked for me even when I was using windows vista on Sony full HD TV. Sorry.

---

### Post by njgriffin on 2009-09-02
That is strange I use the HDMI connection in Vista constantly connected to a Panasonic HDTV.  Never had any problems other than making Vista remember to use it all the time so disabled the other speakers in the sounds panel in control panel.

N

---

### Post by pedja_portugalac on 2009-09-27
Audio work out of the box in Karmic Koala 9.10. Yesterday I tried daily image of Karmic Koala and it just works out of the box.

If for any reason you can't wait for 9.10 to come officially out, or you must remain on older Ubuntu version, you can install latest alsa-driver with help of this script 
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

If for any reason after installation you have no sound, after unmuting sound in gnome and putting everything in alsamixer to the max, then you should change original settings in /etc/modprobe.d/alsa-base.conf to this
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
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10
```   

and reboot to take effect.

---

### Post by pedja_portugalac on 2010-04-08
Audio works out of the box in Ubuntu 10.04 Lucid Lynx. Unmute and that's all. Thanks Ubuntu and alsa.

---

### Post by steward on 2010-12-04
Hello...I got SOny vaio VPCEA12EG and the sound card is Realtek High Definition Audio High...I ve installed UBUNTU 10.04 ..But Ican not hear anything...When I try alsamixer..all the bar s are high but the thing is, it has detected wrong driver named intel ...Another point is that I can hear from my headphone jack ofcourse very hard....the sound is too weak,,,,,But I can not hear anything from the speakers.....would u plz help....

---

### Post by steward on 2010-12-04
I ve read [http://ubuntuforums.org/showthread.php?t=551615&page=4](http://ubuntuforums.org/showthread.php?t=551615&page=4)

and I tried to execute 

cd alsa-driver-1.0.16.tar
./configure --with-cards=hda-intel
make
sudo make install

but I got a lot of errors..


/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2501: error: expected ‘)’ before ‘pid’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2502: error: expected ‘)’ before ‘pid’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2536: error: expected declaration specifiers or ‘...’ before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘add_rchar’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2538: error: ‘struct task_struct’ has no member named ‘ioac’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2538: error: ‘amt’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2541: error: expected declaration specifiers or ‘...’ before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘add_wchar’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2543: error: ‘struct task_struct’ has no member named ‘ioac’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2543: error: ‘amt’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘inc_syscr’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2548: error: ‘struct task_struct’ has no member named ‘ioac’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘inc_syscw’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2553: error: ‘struct task_struct’ has no member named ‘ioac’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘task_rlimit’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2602: error: ‘const struct task_struct’ has no member named ‘signal’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2602: error: ‘const struct task_struct’ has no member named ‘signal’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2602: warning: type defaults to ‘int’ in declaration of ‘type name’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘task_rlimit_max’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2608: error: ‘const struct task_struct’ has no member named ‘signal’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2608: error: ‘const struct task_struct’ has no member named ‘signal’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2608: warning: type defaults to ‘int’ in declaration of ‘type name’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘rlimit’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2613: error: ‘current’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h: In function ‘rlimit_max’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sched.h:2618: error: ‘current’ undeclared (first use in this function)
In file included from hpetimer.c:28:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:26:51: error: asm/semaphore.h: No such file or directory
In file included from hpetimer.c:28:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h: At top level:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:151: error: field ‘controls_rwsem’ has incomplete type
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:315: error: expected declaration specifiers or ‘...’ before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:316: error: expected declaration specifiers or ‘...’ before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:367: error: expected declaration specifiers or ‘...’ before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h: In function ‘snd_timestamp_now’:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:474: error: ‘struct timespec’ has no member named ‘tv_sec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:474: error: ‘struct timeval’ has no member named ‘tv_sec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:475: error: ‘struct timespec’ has no member named ‘tv_nsec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:475: error: ‘struct timeval’ has no member named ‘tv_usec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:477: error: ‘struct timespec’ has no member named ‘tv_nsec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h: In function ‘snd_timestamp_zero’:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:482: error: ‘struct timespec’ has no member named ‘tv_sec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:483: error: ‘struct timespec’ has no member named ‘tv_nsec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h: In function ‘snd_timestamp_null’:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:488: error: ‘struct timespec’ has no member named ‘tv_sec’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/core.h:488: error: ‘struct timespec’ has no member named ‘tv_nsec’
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:28,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/timer.h:26,
                 from hpetimer.c:29:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/ioctl.h:4:23: error: asm/ioctl.h: No such file or directory
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/timer.h:26,
                 from hpetimer.c:29:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:42:2: error: #error "Unsupported endian..."
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/timer.h:26,
                 from hpetimer.c:29:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h: At top level:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:145: error: expected specifier-qualifier-list before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:150: warning: implicit declaration of function ‘_IOR’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:150: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:151: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:152: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:153: warning: implicit declaration of function ‘_IOW’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:153: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:361: error: expected specifier-qualifier-list before ‘u_int32_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:404: error: expected specifier-qualifier-list before ‘off_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:465: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:466: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:467: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:468: warning: implicit declaration of function ‘_IOWR’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:468: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:469: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:470: warning: implicit declaration of function ‘_IO’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:470: error: enumerator value for ‘SNDRV_PCM_IOCTL_HW_FREE’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:471: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:472: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:473: error: expected expression before ‘sndrv_pcm_sframes_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:474: error: enumerator value for ‘SNDRV_PCM_IOCTL_HWSYNC’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:475: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:476: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:477: error: enumerator value for ‘SNDRV_PCM_IOCTL_PREPARE’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:478: error: enumerator value for ‘SNDRV_PCM_IOCTL_RESET’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:479: error: enumerator value for ‘SNDRV_PCM_IOCTL_START’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:480: error: enumerator value for ‘SNDRV_PCM_IOCTL_DROP’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:481: error: enumerator value for ‘SNDRV_PCM_IOCTL_DRAIN’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:482: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:483: error: expected expression before ‘sndrv_pcm_uframes_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:484: error: enumerator value for ‘SNDRV_PCM_IOCTL_RESUME’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:485: error: enumerator value for ‘SNDRV_PCM_IOCTL_XRUN’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:486: error: expected expression before ‘sndrv_pcm_uframes_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:487: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:488: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:489: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:490: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:491: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:492: error: enumerator value for ‘SNDRV_PCM_IOCTL_UNLINK’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:536: error: expected specifier-qualifier-list before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:545: error: expected specifier-qualifier-list before ‘size_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:551: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:552: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:553: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:554: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:555: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:556: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:666: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:667: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:668: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:669: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:670: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:671: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:672: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:673: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:674: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:675: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:677: error: enumerator value for ‘SNDRV_TIMER_IOCTL_START’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:678: error: enumerator value for ‘SNDRV_TIMER_IOCTL_STOP’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:679: error: enumerator value for ‘SNDRV_TIMER_IOCTL_CONTINUE’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:680: error: enumerator value for ‘SNDRV_TIMER_IOCTL_PAUSE’ is not an integer constant
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:795: error: expected specifier-qualifier-list before ‘pid_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:848: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:849: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:850: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:851: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:852: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:853: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:854: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:855: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:856: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:857: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:858: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:859: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:860: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:861: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:862: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:863: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:864: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:865: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:866: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:867: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:868: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:869: error: expected expression before ‘int’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:925: error: expected expression before ‘struct’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/asound.h:926: error: expected expression before ‘struct’
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:4:22: error: asm/poll.h: No such file or directory
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:368,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:21: error: expected ‘)’ before ‘dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘old_encode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘old_decode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:36: error: expected ‘)’ before ‘dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘new_encode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘new_decode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:55: error: expected ‘)’ before ‘dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘huge_encode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘huge_decode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:70: error: expected ‘)’ before ‘dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysv_encode_dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:80: error: expected ‘)’ before ‘dev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/kdev_t.h:85: error: expected ‘)’ before ‘dev’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:382,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fiemap.h:17: error: expected specifier-qualifier-list before ‘__u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fiemap.h:28: error: expected specifier-qualifier-list before ‘__u64’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:415: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:416: error: expected declaration specifiers or ‘...’ before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:451: error: expected specifier-qualifier-list before ‘umode_t’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:470,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:107: error: expected specifier-qualifier-list before ‘__u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:128: error: expected specifier-qualifier-list before ‘__u64’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:176,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:470,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/dqblk_xfs.h:51: error: expected specifier-qualifier-list before ‘__s8’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/dqblk_xfs.h:138: error: expected specifier-qualifier-list before ‘__u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/dqblk_xfs.h:144: error: expected specifier-qualifier-list before ‘__s8’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:470,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:182: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:205: error: expected specifier-qualifier-list before ‘time_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:274: error: expected specifier-qualifier-list before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:328: error: expected declaration specifiers or ‘...’ before ‘qid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:329: error: expected declaration specifiers or ‘...’ before ‘qid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:332: error: expected declaration specifiers or ‘...’ before ‘qid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:333: error: expected declaration specifiers or ‘...’ before ‘qid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/quota.h:384: error: field ‘dqptr_sem’ has incomplete type
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:519: error: expected specifier-qualifier-list before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:523: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_copy_from_user_atomic’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:525: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_copy_from_user’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:527: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:528: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:529: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_single_seg_count’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:533: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:533: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘iov_iter_init’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:537: error: ‘struct iov_iter’ has no member named ‘iov_offset’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:538: error: ‘struct iov_iter’ has no member named ‘count’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:538: error: ‘count’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:538: error: ‘written’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:540: error: too many arguments to function ‘iov_iter_advance’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:543: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_count’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:558: error: expected specifier-qualifier-list before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:585: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:588: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:595: error: expected specifier-qualifier-list before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:613: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:617: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:646: error: expected specifier-qualifier-list before ‘dev_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:730: error: expected specifier-qualifier-list before ‘uid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:822: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘i_size_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:850: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘i_size_write’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:861: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:861: error: ‘i_size’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘iminor’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:867: error: ‘const struct inode’ has no member named ‘i_rdev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘imajor’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:872: error: ‘const struct inode’ has no member named ‘i_rdev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:881: error: expected specifier-qualifier-list before ‘uid_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:896: error: expected specifier-qualifier-list before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:925: error: expected specifier-qualifier-list before ‘atomic_long_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1033: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1034: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1038: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1039: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1040: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1041: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1042: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1043: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1044: warning: ‘struct file_lock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1045: warning: ‘struct file_lock’ declared inside parameter list
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h:130,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs_fs_i.h:6,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1057,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sunrpc/msg_prot.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rpc_authflavor_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/sunrpc/msg_prot.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rpc_fraghdr’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/sunrpc/msg_prot.h:193,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h:130,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs_fs_i.h:6,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1057,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/inet.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘in_aton’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/inet.h:55: error: expected declaration specifiers or ‘...’ before ‘u8’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/inet.h:56: error: expected declaration specifiers or ‘...’ before ‘u8’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs_fs_i.h:6,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1057,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h: In function ‘nfs_compare_fh’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h:148: error: too many arguments to function ‘memcmp’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h: In function ‘nfs_copy_fh’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs.h:154: error: too many arguments to function ‘memcpy’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1057,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs_fs_i.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/nfs_fs_i.h:14: error: expected specifier-qualifier-list before ‘u32’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1070: error: expected specifier-qualifier-list before ‘loff_t’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1095,
                 from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fcntl.h:4:23: error: asm/fcntl.h: No such file or directory
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1100: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1101: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1104: warning: ‘struct flock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1106: warning: ‘struct flock’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1137: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1138: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1303: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_getown’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1323: error: expected specifier-qualifier-list before ‘dev_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1420: error: expected declaration specifiers or ‘...’ before ‘dev_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1447: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1448: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1448: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1448: error: expected declaration specifiers or ‘...’ before ‘u32’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1449: error: expected declaration specifiers or ‘...’ before ‘u32’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1473: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1473: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1489: error: expected specifier-qualifier-list before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1524: error: expected declaration specifiers or ‘...’ before ‘dev_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1535: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1536: error: expected specifier-qualifier-list before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1548: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rw_copy_check_uvector’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1553: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1554: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_readv’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1557: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_writev’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1581: error: expected specifier-qualifier-list before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘inode_inc_iversion’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1729: error: ‘struct inode’ has no member named ‘i_lock’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1730: error: ‘struct inode’ has no member named ‘i_version’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1731: error: ‘struct inode’ has no member named ‘i_lock’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘file_accessed’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1737: error: ‘struct file’ has no member named ‘f_flags’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1737: error: ‘O_NOATIME’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1818: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1818: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1825: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1825: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘__mandatory_lock’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1834: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘mandatory_lock’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1844: error: ‘struct inode’ has no member named ‘i_sb’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1856: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘locks_verify_truncate’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1858: error: ‘struct inode’ has no member named ‘i_flock’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1861: error: ‘size’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1861: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1861: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1862: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1862: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1863: error: ‘struct inode’ has no member named ‘i_size’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1864: error: too many arguments to function ‘locks_mandatory_area’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘break_lease’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1870: error: ‘struct inode’ has no member named ‘i_flock’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1917: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1919: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1920: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1951: warning: parameter names (without types) in function declaration
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1953: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1956: error: expected ‘)’ before ‘fmode_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1992: warning: ‘struct gendisk’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:1993: warning: ‘struct gendisk’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2002: error: expected ‘)’ before ‘*’ token
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2003: error: expected ‘)’ before ‘unsigned’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2009: error: expected ‘)’ before ‘unsigned’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2010: error: expected declaration specifiers or ‘...’ before ‘off_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2029: error: expected ‘)’ before ‘char’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2034: error: expected declaration specifiers or ‘...’ before ‘off_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2040: error: expected declaration specifiers or ‘...’ before ‘umode_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2040: error: expected declaration specifiers or ‘...’ before ‘dev_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2064: warning: ‘struct gendisk’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2065: warning: ‘struct gendisk’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2068: warning: ‘struct gendisk’ declared inside parameter list
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘invalidate_remote_inode’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2082: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2082: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2083: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2084: error: ‘struct inode’ has no member named ‘i_mapping’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2093: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2094: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2097: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2097: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2101: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2101: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2103: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2103: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2106: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2106: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2108: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2108: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘execute_ok’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2122: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2122: error: ‘struct inode’ has no member named ‘i_mode’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘put_write_access’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2129: error: ‘struct inode’ has no member named ‘i_writecount’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: In function ‘allow_write_access’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2134: error: ‘struct inode’ has no member named ‘i_writecount’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2145: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘find_inode_number’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2155: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘default_llseek’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2157: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_llseek’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2164: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iunique’
In file included from /lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:12,
                 from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2213: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2213: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2214: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_aio_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2215: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__generic_file_aio_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2217: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_aio_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2218: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_direct_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_buffered_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2222: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_sync_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2223: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_sync_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2225: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2228: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blkdev_aio_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_splice_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘default_file_splice_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2237: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_splice_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2239: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_splice_sendpage’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2241: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2242: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2246: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_llseek’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2247: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_llseek’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_llseek_unlocked’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2261: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2268: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__blockdev_direct_IO’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2288: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO_no_locking’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2297: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO_own_locking’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2323: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2324: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2325: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2326: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inode_get_bytes’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2327: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2339: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2340: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2342: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2343: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2350: warning: parameter names (without types) in function declaration
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2355: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dcache_dir_lseek’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2369: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2372: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_read_dir’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2385: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_read_from_buffer’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2398: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2407: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘parent_ino’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2424: error: expected specifier-qualifier-list before ‘ssize_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2431: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2432: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_transaction_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2436: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2475: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2475: error: expected declaration specifiers or ‘...’ before ‘u64’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2478: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_attr_read’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2480: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_attr_write’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2485: error: expected declaration specifiers or ‘...’ before ‘size_t’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/fs.h:2485: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:13:25: error: asm/uaccess.h: No such file or directory
In file included from /home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:25,
                 from hpetimer.c:30:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h: In function ‘get_fd_set’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:107: warning: implicit declaration of function ‘copy_from_user’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:107: error: ‘EFAULT’ undeclared (first use in this function)
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:109: error: too many arguments to function ‘memset’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h: In function ‘set_fd_set’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:117: warning: implicit declaration of function ‘__copy_to_user’
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h: In function ‘zero_fd_set’:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/poll.h:124: error: too many arguments to function ‘memset’
In file included from hpetimer.c:30:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h: At top level:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:75: error: expected specifier-qualifier-list before ‘mode_t’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h: In function ‘snd_info_set_text_ops’:
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:142: error: ‘snd_info_entry_t’ has no member named ‘private_data’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:143: error: ‘snd_info_entry_t’ has no member named ‘c’
/home/sadra/alsa-driver-1.0.9rc4a/include/sound/info.h:144: error: ‘snd_info_entry_t’ has no member named ‘c’
In file included from hpetimer.c:31:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/hpet.h: At top level:
/lib/modules/2.6.32-26-generic-pae/build/include/linux/hpet.h:13: error: expected specifier-qualifier-list before ‘u64’
hpetimer.c: In function ‘snd_hpet_open’:
hpetimer.c:41: warning: implicit declaration of function ‘hpet_register’
hpetimer.c:44: warning: implicit declaration of function ‘hpet_control’
hpetimer.c:44: error: expected expression before ‘unsigned’
hpetimer.c: In function ‘snd_hpet_close’:
hpetimer.c:51: warning: implicit declaration of function ‘hpet_unregister’
hpetimer.c:52: error: invalid use of undefined type ‘struct hpet_task’
hpetimer.c: In function ‘hpetimer_init’:
hpetimer.c:88: error: ‘EINVAL’ undeclared (first use in this function)
hpetimer.c:99: error: invalid use of undefined type ‘struct hpet_task’
hpetimer.c:100: error: invalid use of undefined type ‘struct hpet_task’
hpetimer.c: At top level:
hpetimer.c:121: warning: excess elements in struct initializer
hpetimer.c:121: warning: (near initialization for ‘__param_frequency’)
hpetimer.c:121: warning: excess elements in struct initializer
hpetimer.c:121: warning: (near initialization for ‘__param_frequency’)
hpetimer.c:121: warning: excess elements in struct initializer
hpetimer.c:121: warning: (near initialization for ‘__param_frequency’)
hpetimer.c:121: warning: excess elements in struct initializer
hpetimer.c:121: warning: (near initialization for ‘__param_frequency’)
hpetimer.c:121: error: extra brace group at end of initializer
hpetimer.c:121: error: (near initialization for ‘__param_frequency’)
hpetimer.c:121: warning: excess elements in struct initializer
hpetimer.c:121: warning: (near initialization for ‘__param_frequency’)
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/home/sadra/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1

what should I do?

---

