---
title: "No sound with snd-hda-intel after jackalope upgrade"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by T1000 on 2009-04-26
I cannot get any sound at all since the jackalope upgrade (64 bits).
The PC is a HP HDX18 laptop.

I could not install the latest 1.0.19 alsa drivers since alsaconf invokes a missing script (update-modules). I do not know where to get it.

I followed the following howto after that:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

"aplay -l" returns the following:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v returns the following:
(...)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3610
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dd000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
(...)

I compiled the alsa drivers (1.018 this time) with module assistant:
sudo module-assistant a-i   alsa-source

It compiled successfully -the progress bar reached 100% with no errors-, but there is still no sound.

Another thing:
/etc/modprobe.d/alsa-base was empty, I tried:
options snd-hda-intel model=hp
   and
options snd-hda-intel model=auto


/etc/modprobe.d/sound is as such:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

Trying all Sound Preferences combinations does not solve anything.

Would anybody have any clue?
Thanks

---

### Post by Triptol on 2009-04-26
Just a guess: maybe you need to unmute your soundcard channels.

 Type 'alsamixer' (without the quotes) and see if the meters are "up".

---

### Post by Triptol on 2009-04-26
BTW: I have the same soundcard and I didn't have to compile anything. The also modules are already included with a default installation.

---

### Post by T1000 on 2009-04-26
No, the meters are up! :)

---

### Post by T1000 on 2009-04-26
The problem is some tinkering may be needed for some laptop models.
What is yours?

---

### Post by linux_tech on 2009-04-26
Try reinstalling alsa base
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
then reboot

---

### Post by T1000 on 2009-04-26
No change after reboot... 

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2Reading package lists... Done

Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
[COLOR="Red"]Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic"[/COLOR]
The following packages will be REINSTALLED:
  alsa-base alsa-utils libasound2 linux-image-2.6.28-11-generic linux-sound-base 
0 packages upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/26.0MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 145870 files and directories currently installed.)
Preparing to replace linux-image-2.6.28-11-generic 2.6.28-11.42 (using .../linux-image-2.6.28-11-generic_2.6.28-11.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.28-11-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace alsa-base 1.0.18.dfsg-1ubuntu8 (using .../alsa-base_1.0.18.dfsg-1ubuntu8_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.18-1ubuntu11 (using .../alsa-utils_1.0.18-1ubuntu11_amd64.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace libasound2 1.0.18-1ubuntu9 (using .../libasound2_1.0.18-1ubuntu9_amd64.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.18.dfsg-1ubuntu8 (using .../linux-sound-base_1.0.18.dfsg-1ubuntu8_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-11.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-11.42 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-11-generic                                                                            
 *  nvidia (180.44)...                                                                                                                            nvidia (180.44): Already installed on this kernel.
                                                                                                                                           [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up libasound2 (1.0.18-1ubuntu9) ...

Setting up linux-sound-base (1.0.18.dfsg-1ubuntu8) ...

Setting up alsa-base (1.0.18.dfsg-1ubuntu8) ...

Setting up alsa-utils (1.0.18-1ubuntu11) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

---

### Post by Triptol on 2009-04-26
Ok, so the modules were wrong...

I have installed the following modules packages:
linux-restricted-modules-generic (it will depend on the latest so this is a save bet).

That might at least fix the modules install problem.

---

### Post by Triptol on 2009-04-26
I have a Dell D830. And I just see that mine is ICH8, you have ICH9. Probably a big difference ;-)

In /etc/modprobe.d/alsa-base.conf I have the following:
```
options snd-intel8x0m index=-2
```
I don't think I put it there though ;-)

/etc/modprobe.d/sound is not on my system

---

### Post by T1000 on 2009-04-26
linux-restricted-modules-generic-2.6.28-11 was already there and was the latest (2.6.28-11.15)

I forced a reinstall with Synaptic package manager though.

The same message occurs when running your command after reboot. This is quite confusing :confused:

---

### Post by T1000 on 2009-04-26
same line in /etc/modprobe.d/alsa-base.conf (different from 
/etc/modprobe.d/alsa-base)

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
**[COLOR="Red"]options snd-intel8x0m index=-2[/COLOR]**
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

### Post by T1000 on 2009-04-26
"sudo modprobe snd-hda-intel" would issue the following
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

/etc/modprobe.d/alsa-base.conf, which is a different file, is as such:
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
[COLOR="Red"]options snd-intel8x0m index=-2[/COLOR]
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2


I tried adding
options snd-hda-intel model=hp
options snd-hda-intel model=auto

which I had found on another thread, with no result, on both
/etc/modprobe.d/alsa-base (previously empty)
/etc/modprobe.d/alsa-base.conf (not empty)

Thanks for any advice

---

### Post by T1000 on 2009-04-26
reinstalling alsa-base, as advised by linux-tech,
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

 issues a warning during processing:
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic

installing linux-restricted-modules-generic, as advised by triptol, does not fix the issue (thanks anyway)

Would anyone have a clue on the way to get  
linux-ubuntu-modules-2.6.28-11-generic?

I could not find it in the package manager

thanks

---

### Post by T1000 on 2009-04-26
since "this would not make matters worse" I also followed the instructions in here

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

no enhancement... :(

---

### Post by tomsa on 2009-04-26
I have been having similar problems.  See this bug on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

I haven't been able to find a fix for this either.

---

### Post by klondike0 on 2009-04-27
I've got the same issue.  When I upgraded from 8.10, the sound was very faint and wouldn't respond to volume changes.  When I did a clean install from a 9.04 i386 desktop disk, sound was broken (the install did fix my resolution issue though :))

In both cases I looked at alsamixer and the 'master' & 'front' fields are at '00' and cannot be changed.  

aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 1263
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at feb3c000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

reinstalling alsa as suggested by the community documentation did not correct the issue:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

---

### Post by linuxinho on 2009-04-30
Hello!

First, sorry for my not perfect English!

HP HDX18. Same Problems!

Since I`ve installed the pulseaudio packages, I have sound (login, system-sound, multimedia players) on headphone jack (on both, the HP HDX18 model has two).

But still, no sound on speakers.

I've tried a lot, but it will not work.

Anybody overcome this problem with the speakers sound output?

It`s frustrating, Multemedia Notebook and no sound.

Greetings, 
linuxihno :sad:

---

### Post by cucisan on 2009-05-06
> **linuxinho said:**
> Hello!

First, sorry for my not perfect English!

HP HDX18. Same Problems!

Since I`ve installed the pulseaudio packages, I have sound (login, system-sound, multimedia players) on headphone jack (on both, the HP HDX18 model has two).

But still, no sound on speakers.

I've tried a lot, but it will not work.

Anybody overcome this problem with the speakers sound output?

It`s frustrating, Multemedia Notebook and no sound.

Greetings, 
linuxihno :sad:


try adding: options snd-hda-intel model=hp-m4 to your /etc/modprobe.d/alsa-base.conf for HDX16/18 problems.. fixed it for me

---

### Post by klondike0 on 2009-05-09
Hey Hey! Sound works on my Portable One laptop!

It appears Alsa was picking the wrong model for the codec to work (ALC660).  I had to find the correct hardware and codec, then play with the parameters until I found one that works (and reboot a bunch of times in the process).

The link that was most useful in fixing this was:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

starting at the section titled: Is ALSA using the correct model?

You can get all your sound related information by running the command below in a terminal, then going to the website link afterward:

wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh


In the end, I modified this file:

/etc/modprobe.d/alsa-base.conf

by adding this line at the end:

options snd-hda-intel model=asus

and rebooted.  Hooray!

---

### Post by davejmet on 2009-05-19
Thank you Klondike0 for this.

Finally got sound on my Dell Vostro running Jaunty.

In /etc/modprobe.d/alsa-base.conf

by adding this line at the end:

options snd-hda-intel model=dell-m42

 and reboot

Regards,  davejmet

---

### Post by isparkes on 2009-05-19
Adding this to the end of my /etc/modprobe.d/alsa-base.conf worked on my HP dv3000

```
options snd-hda-intel model=hp-m4
```

In addition I also played around with 

```
alsamixer
```

turning the volume up on everything (but unsure if it did anything).

Thanks

---

### Post by V8pedals on 2009-05-20
> **T1000 said:**
> I cannot get any sound at all since the jackalope upgrade (64 bits).
The PC is a HP HDX18 laptop.

I could not install the latest 1.0.19 alsa drivers since alsaconf invokes a missing script (update-modules). I do not know where to get it.

I followed the following howto after that:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

"aplay -l" returns the following:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v returns the following:
(...)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3610
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at dd000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
(...)

I compiled the alsa drivers (1.018 this time) with module assistant:
sudo module-assistant a-i   alsa-source

It compiled successfully -the progress bar reached 100% with no errors-, but there is still no sound.

Another thing:
/etc/modprobe.d/alsa-base was empty, I tried:
options snd-hda-intel model=hp
   and
options snd-hda-intel model=auto


/etc/modprobe.d/sound is as such:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

Trying all Sound Preferences combinations does not solve anything.

Would anybody have any clue?
Thanks
Try this after much research I came across a post that advised me to do this

find out what soundcard you have with 
#lspci

In #/etc/modprobe.d/alsabase
add this line to the end of alsabase
options snd-hda-intel model=auto    "this looks in bios to set it up"

---

### Post by dayers on 2009-05-26
I can boot from either Ubuntu 7.?? (factory install) or Xubuntu 9.04 on my Dell Inspiron desktop. The first has sound; the latter does not. 

I ran the ALSA Information Script on both distributions. On the old Ubuntu, which has sound, a sound server is detected:

!!Sound Servers on this system
!!----------------------------

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - yes

Running the script on the silent Xubuntu tells me that there are no Sound Servers running.

A clue (maybe)

dave@surprise:~$ ls /usr/bin |grep esd
esdcat
esdctl
esddsp
esdfilt
esdloop
esdmon
esdplay
esdrec
esdsample
dave@surprise:~$ 

It appears that no sound servers were started when Xubuntu booted. Can anyone suggest where I go from here?

---

### Post by dayers on 2009-05-27
I'm making a fresh start trying to troubleshoot my sound problem, and I'll try to step through the SoundTroubleshooting article referred to by several of you. I have also tried suggestions in earlier posts to the best of my understanding, which ain't much. I'm glad that someone, at least, has found the magic wand.

I am starting with a fresh install from a Kubuntu 9.04 bootable disk (burned on 5-19-09). I am running on a Dell Inspiron desktop with factory installed Ubuntu 7.04. It's sound works fine. Kubuntu has no sound at all since upgrade from 8.10.

I'll post my progress as I go along in hopes that it will save someone the many hours I have spent trying to get the sound back.

Dave

---

### Post by dayers on 2009-05-28
After carefully working my way down to "Manual Installation in SoundTroubleshooting article, still no sound. I believe I correctly identified the codec for my Dell 530 as Realtek ALC888 and the Model as 6stack-dell. To test sound I am using 

dave@Surprise:~$ aplay Noise.wav
Playing WAVE 'Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
dave@Surprise:~$

I guess my next step is filing a bug report, as suggested. If this results in some noise, I'll report back.

---

### Post by linuxinho on 2009-06-11
@cucisan

> Etry adding: options snd-hda-intel model=hp-m4 to your /etc/modprobe.d/alsa-base.conf for HDX16/18 problems.. fixed it for meAfter a long time, ignoring my sound card proplem,
I came back to the forum and found your answer.

YEAH, IT WORKS!  GREAT!

:popcorn::D

BIG THANKS!

---

