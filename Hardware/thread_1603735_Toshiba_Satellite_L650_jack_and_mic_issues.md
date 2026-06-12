---
title: "Toshiba Satellite L650 jack and mic issues"
date: 2010-10-23
forum: Hardware
---

### Post by mariost on 2010-10-23
After I installed a bios update due to ACPI problems, it all went okay except I cant use internal microphone, external microphone and the audio output jack. I've seen threads about this on different laptops, tried some of the solutions, they didnt work for me for varying reasons. So, here are the specs:
Laptop Toshiba Satellite L650-10H
Linux Ubuntu 10.10 2.6.35-22-generic
```
discharge@discharge-lap:/$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

``````
discharge@discharge-lap:~/downloads$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
discharge@discharge-lap:~/downloads$ cat /etc/modprobe.d/sound.conf
cat: /etc/modprobe.d/sound.conf: No such file or directory

``````
/etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```Tried adding 
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
after that tried: alsa options snd-hda-intel model=auto
to /etc/modprobe.d/alsa-base.conf , no effect. 
Tried using [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) but on the step with passing "sudo ./AlsaUpgrade-1.0.23-2.sh -c" it returns an error:
```
***************************************************************************
*  Alsa packages(drivers/lib/util/firmware/oss) will be compiled
***************************************************************************

***************************************************************************
*  Prepare for compilation and installation...
***************************************************************************

***************************************************************************
*  alsa-lib-1.0.23 not found
***************************************************************************
```Tried installing linuxant driver as supposed [here]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") only to get this:
```
discharge@discharge-lap:~/downloads$ sudo dpkg -i alsa-driver-linuxant_1.0.23.0_all.deb 
(Reading database ... 204479 files and directories currently installed.)
Preparing to replace alsa-driver-linuxant 1.0.23.0 (using alsa-driver-linuxant_1.0.23.0_all.deb) ...
Unpacking replacement alsa-driver-linuxant ...
Setting up alsa-driver-linuxant (1.0.23.0) ...
Building modules for the 2.6.35-22-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3695.log
dpkg: error processing alsa-driver-linuxant (--install):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 alsa-driver-linuxant
```Okay, provided everything that might be useful I can think of, hope it is enough to help you identify the problem :) By the way before I did the bios upgrade when I played audio the laptops' speakers used to play along with the external ones, which I considered a nice thing. Hope after fix i have a chance to choose to use or not to use that functionality. Thank you in advance ;)

---

### Post by mariost on 2010-10-24
Okay, looks like nobody replies because there is no answer. In several places i have read that the problem is that 10.10 is not suited for that linuxant driver. So the thing I did is sudo apt-get remove --purge <anything starting with alsa>; sudo apt-get install --reinstall linux-image-2.6.35-22 . That got my audio to starting position, working only internal speakers. Until there is a fix, I will just use my old 10.04 kernel which has no such problems. I wont mark the thread as solved because that is yet to be solved, my way is just a workaround.

---

### Post by njsharp on 2010-11-04
FYI:

I think some of my problems on a Toshiba Satellite L640 BIOS 1.5 noted at:

[http://ubuntuforums.org/showthread.php?t=1613746](http://ubuntuforums.org/showthread.php?t=1613746)

are similar.  I did not change the BIOS but just installed 10.10 and found the headphone socket did nothing (no sound on phones, sound still coming from speakers) and the webcam microphone did not appear anywhere (camera worked though).

---

### Post by Crimbo on 2010-11-08
Bug report filed...

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/666572]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/666572")

...If you would like to subscribe to it, and select that it affects you (couple lines down from the main title).

---

### Post by mariost on 2010-11-14
Here's the solution, followed two links and here is it!  Works flawlessly after install and reboot ;)
```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```
*[original link](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)*
PS: flawlessly=mic working, sound through speakers OR headphones, depending on whether external audio jack is plugged!

---

### Post by Crimbo on 2010-11-14
No joy for me :(

...and thus, I don't think this thread can be labeled as solved!

---

### Post by ersgupta on 2010-11-15
same problem here... i hav toshiba satellite L650... n speakers r working but nt d headphone... :(

---

### Post by mariost on 2010-11-16
I just removed the said driver, which was followed by reappearing of the bug. Installing it again fixed it. So I can confirm that at least in my case, this solution does the magic, thus the solved status.

---

### Post by Crimbo on 2010-11-16
Still no joy. I've tried removing the package completely and then re-installing it, trying alternate packages, making sure it's the latest alsa drivers, but it made no difference.

I'm wondering if it's because I may have a slightly different model of laptop, or maybe because I'm currently Maverick Meerkat.

My laptop is: L650-165

If you could give a step by step process of what you did to get it working mariost? i.e. reboots.

---

### Post by mariost on 2010-11-18
After i removed the driver, restarted. Tried getting sound from audacious, no sound, checked settings using right click on the gnome sound icon > sound preferences. There i checked input and output to see there is no sound (think internal audio was gone but dont remember). Installed back the package, restarted, and sound from every source was working. Opened the sound preferences again, output volume wasnt muted, in hardware tab i have Internal Audio & Redwood HDMI audio (which doesnt matter because i dont ever use it. On the bottom there is profile, which is set to Analog stereo duplex. Input tab, microphone again wasnt muted and showed the microphone input level. Its set to unamplified 100%. Output tab, Internal Audio Analog Stereo was selected, leaving Redwood HDMI audio unchecked.


```
discharge@discharge-lap:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
``````
discharge@discharge-lap:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Alsa try using alsamixer , and installing **alsa-base alsa-oss alsa-utils**
PS: Ah something that might be causing ur prob! Uninstall everything related to **oss***. Recently installed it to try to make quake3 sound work, and on sound settings got Dummy audio instead of the internal one, with no sound support at all.
Many times its up to installing/deinstalling packages. 
Last resort is try **sudo apt-get install --reinstall linux-image-$(uname -r)**,
helped me once, though it fetches a lot of unneeded stuff.
Btw, problem is not Maverick Meercat (10.10), as im using it too. But its true that with some of the older kernels i never had this problem.
Good luck!

---

### Post by Crimbo on 2010-11-18
YES!! IT WORKS!! :.(

arr I'm so happy! You're a star Mariost! I've been scratching my head about this for weeks, and have been forced to use windows for headphone sound. Now I don't need to use my tinny laptop speakers!
---------

I completely removed anything alsa related, and then rebooted, and the sound still seemed to work through the standard speakers, without the driver. I then noticed I hadn't removed alsa-oss, alsa-utils, and anything oss, but that didn't make any difference.

(weird?)

So anyway, after the reboot, I installed the driver again like you stated in a previous post...

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

and it didn't work... hmmm.

So I looked carefully at the terminal code, and notice an error writing to (what I think was called) linux-conf-variant. So I removed it, and then the system came to slow crash (why I couldn't note the package name).

I rebooted (still no headphone sound) and reinstalled the alsa driver, kinda giving up at this point and then my mate distracted me with a youtube link. Whilst watching that, I thought to myself, that sound seems funny, and then realised it was coming from my headphones!! :D

**For the mic**, it at first wasn't working, but then I realised I had to checkbox tick the 'Rec.' in the Alsamixer window, and 'Analog Mic Boost' (which I later found out).
---------

I assume what caused the problem, of the jack-sense and mic, was ubuntu wasn't picking up the alsa driver(s). I don't know if that ?linux-conf-variant? package was causing the problem.
**If anyone finds the same error, please state the correct package name!**

---

### Post by aslangencer on 2011-01-05
This worked for me too on Satellite-L650. No other action needed.
Thanks mariost.

---

### Post by king james II on 2011-02-11
worked for my toshiba satellite T135D-S1324 RT. :KSCHEERS MARIOST:KS

---

### Post by king james II on 2011-02-11
> **For the mic**, it at first wasn't working, but then I realised I  had to checkbox tick the 'Rec.' in the Alsamixer window, and 'Analog Mic  Boost' (which I later found out).

Still stumped on the mic issue. What do you tick the checkbox? In the Alsa terminal window or a different one?

---

