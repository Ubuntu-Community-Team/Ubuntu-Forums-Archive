---
title: "Acer Aspire 5710WLMi"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Dave Crowhurst on 2007-08-22
I have been sitting on the fence for a while, and thinking seriously about making the switch from OSX to Ubuntu. The obviousy easy choice for a total Linux/Ubuntu newb like me would be to buy a Dell Inspiron 6400n, but i'm not really feeling the love for the design :-s  My G3 PPC iBook is a cute icke machine, and i'd like something that not only runs well but looks (to me) good as well :D

I like the design of the new Acer 'gemstone' laptops. I have looked around and found the specs for the Aspire 5710WLMi

> The Aspire 5710WLMi is part of Acer's new Gemstone range and is designed using a combination of gloss and matt black on the casing giving it stylish and distinctive look.

This is a fast and powerful laptop featuring Intel's Core 2 Duo Processor and 1GB of RAM, this makes it ideal for surfing the web, checking emails, downloading films and music, creating word and excel documents, storing your home photo's and more.

Processor: Powerful Intel Core 2 Duo T5500 Processor
RAM: 1024MB fast DDR2 RAM - Low cost RAM upgrade call for details
Hard Drive: 80GB Hard Drive for file storage
Screen: 15.4" WXGA TFT Display with Acer CrystalBrite technology
Optical Drive: DVD Re-writer (DVD SuperMulti)
Graphics: Shared Graphics
Wireless LAN: 802.11b/g
Card Reader: 5 in 1 Memory Card Reader
3 x USB 2.0 Ports

I have looked around the forums and the Intel GMA 950 seems to be compatible with Feisty. I am waiting to hear back from Acer as to the make/model of the Sound Card and Wireless Card. Is there anything obvious from the above specs that looks like it might be a problem to get working? I know the 5 in 1 card reader is probably not going to work, which is a shame but not a deal breaker. 

I am wanting to have this machine as Ubuntu only rather than a dual boot Vista/Ubuntu. I would also like to use compiz fusion/beryl desktop effects :) That doesn't seem to be a problem for  the GMA 950.

---

### Post by horned0wl on 2007-08-22
Depending on the wireless card in the system, you might have some trouble there -- the same trouble most folk are having with Broadcom's 43xx series wireless cards... 

I'm running an an AMD-centric Acer Aspire 3050 with 1GB RAM, and even have my Lexmark z35 printer working with it, (Ubuntu 7.04) but, for my life, I can't get wireless networking (or internet) to work...

Cheers;

---

### Post by Dave Crowhurst on 2007-08-23
Here are the full tech specs [http://www.acer.co.uk/acereuro/page9.do?sp=page4&dau34.oid=25376&UserCtxParam=0&GroupCtxParam=0&dctx1=17&CountryISOCtxParam=UK&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+Kingdom&crc=2509576497]("http://www.acer.co.uk/acereuro/page9.do?sp=page4&dau34.oid=25376&UserCtxParam=0&GroupCtxParam=0&dctx1=17&CountryISOCtxParam=UK&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+Kingdom&crc=2509576497")

> 
[COLOR="Orange"]Processor & Chipset[/COLOR]
Intel® Centrino® Duo mobile technology, featuring:
Intel® Core™ 2 Duo processor with up to 4MB L2 Cache

Mobile Intel® 945GM/945PM Express chipset

Intel® PRO/Wireless 3945ABG network connection (dual-band tri-mode 802.11a/b/g) Wi-Fi CERTIFIED® solution, supporting Acer SignalUp™ wireless technology


[COLOR="orange"]Storage[/COLOR]
		HD DVD drive or 
DVD-Super Multi double-layer drive

		5-in-1 card reader, supporting Secure Digital (SD), MultiMediaCard (MMC), Memory Stick® (MS), Memory Stick PRO™ (MS PRO), xD-Picture Card™ (xD)



[COLOR="orange"]Graphics[/COLOR]
		
		Mobile Intel® 945GM Express chipset with integrated 3D graphics, featuring Intel® Graphics Media Accelerator (GMA) 950, up to 224 MB of shared system memory*, supporting Microsoft® DirectX® 9.0, PCI Express®
(* depending on size of system memory)

[COLOR="orange"]Multimedia[/COLOR]
		Dolby® certified surround sound system with two built-in stereo speakers (2 W )

		Dolby® Home Theater audio enhancement featuring Dolby® Digital, Dolby® Digital Live, Dolby® PRO LOGIC II, Dolby® Digital Stereo Creator, Dolby® Headphone, Dolby® Virtual Speaker technologies

		Intel® High Definition audio support

		S/PDIF (Sony/Philips Digital Interface) support for digital speakers

		MS Sound compatible

		Built-in microphone


[COLOR="orange"]Communication[/COLOR]


		Intel® PRO/Wireless 3945ABG network connection (dual-band tri-mode 802.11a/b/g) or 3945BG network connection (dual-mode 802.11b/g) Wi-Fi CERTIFIED® solution, supporting Acer SignalUp™ wireless technology

		Gigabit Ethernet, Wake-on-LAN ready

		56K ITU V.92 with PTT approval, Wake-on-Ring ready

		Bluetooth® 2.0+EDR (Enhanced Data Rate) 
(manufacturing option)


[COLOR="orange"]I/O Interfaces[/COLOR]
		1 x ExpressCard™/54 slot

		5-in-1 card reader (SD, MMC, MS, MS PRO, xD)

		 4 x USB 2.0 ports

		1 x External display (VGA) port

		1x S-video/TV-out (NTSC/PAL) port

		1 x Headphone/speaker/line-out jack with S/PDIF support

		1 x microphone-in jack

		1 x line-in jack

		1 x Ethernet (RJ-45) jack

		1 x Modem (RJ-11) port

		1 x DC-in jack for AC adapter



My main concern was the network and sound cards. I have had a search around these forums and the Intel PRO/Wireless 3945ABG should not be a problem to get working, it seems that 7.04 supports this right out of the box (?)

I think the sound card is made by Realtek. It seems that there are problems with muted sound. I found a thread that pointed towards this HOW-TO

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

And these threads...
[http://ubuntuforums.org/showthread.php?p=3208377](http://ubuntuforums.org/showthread.php?p=3208377)
[http://ubuntuforums.org/showthread.php?t=244624](http://ubuntuforums.org/showthread.php?t=244624)
[http://wisconsinloco.ubuntuforums.org/showthread.php?t=516810](http://wisconsinloco.ubuntuforums.org/showthread.php?t=516810)

So i'm almost 100% sure that even a complete newb, with the help of google, these forums, and some assistance from the community here, should be able to get this machine up and running. The only problem I can think of is the 5-in-1 card reader, and I have yet to see a fix for that. 

I'd appreciate your feedback before I place my order :)

---

### Post by Dave Crowhurst on 2007-08-24
Should I install the 32 bit or 64 bit version of 7.04 on to this machine?

---

### Post by Dave Crowhurst on 2007-08-29
Laptop arrived today :D

Here is what i've done so far...

[LIST]
[*]Set up Vista
[*]Install iTunes
[*]Install Quicktime
[*]Uninstall 90day Norton Trial
[*]Unistall Office trial
[/LIST]

Rebooted system. 

Boot system using Live CD  AMD64 bit version of 7.04.
Checked CD for errors.
Start Ubuntu from Live CD.

What works out of the box from Live CD...
[LIST]
[*]Wireless networking
[*]Volume scroll wheel
[*]Desktop Effects
[/LIST]

Things that will need some work when I do install Ubuntu...
[LIST]
[*]Screen resolution defaults to 1024 x 768 whereas it is 1280 x 800 in Vista.
[*]No sound
[/LIST]

I am going to burn a Vista recovery disk before I partition the drive and install Ubuntu.

---

### Post by Zorael on 2007-08-29
Brief warning about the Intel 3945ABG chipset; It's proving to be [amazingly difficult](https://bugs.launchpad.net/ubuntu/+bug/134515) to make it work satisfactorily for some people, including me. I figured out some workarounds to be able to use it, but when it breaks (randomly) and you're not there to make the effort to fix it, it'll remain broken until such time.

---

### Post by horned0wl on 2007-08-29
> **Dave Crowhurst said:**
> Laptop arrived today :D

Things that will need some work when I do install Ubuntu...
[LIST]
[*]Screen resolution defaults to 1024 x 768 whereas it is 1280 x 800 in Vista.
[*]No sound
[/LIST]

I am going to burn a Vista recovery disk before I partition the drive and install Ubuntu. you 

Ok...  I've discovered that in the 2.6.20-16 and -17 Kernels, sound doesn't work.  However, if you can step back to the -15 Kernel, and use the ALSA sound mixer, sound works quite nicely.  If you start by loading Ubuntu 6.10, then upgrading to 7.04, Keep the -15 Kernel in Grub, and boot to it manually, rather than auto-booting to -16 or -17.

Cheers;

---

### Post by Dave Crowhurst on 2007-08-30
Thanks for the advice. As yet I [haven't even been able to set up a dual boot install]("http://ubuntuforums.org/showthread.php?t=538693").

---

### Post by Dave Crowhurst on 2007-09-01
I now have a working dual boot Vista/Ubuntu thanks to Wubi :)

Sound does not work. I tried the HOWTO [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but still not working.

Screen resolution only allowed 1024 x 768 rather than 1280 x 800. I have fixed this using
```
sudo apt-get install xserver-xorg-video-intel
```

Unlike Vista Home Premium, Ubuntu can network quite easily with my Mac.

---

### Post by Dave Crowhurst on 2007-09-01
Still no fix for the sound (or lack of sound).

I have tried this fix [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and where says...

```
gksudo gedit /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack
```

...I have replace "3stack" with ACER (as [suggested in this thread]("http://ubuntuforums.org/showthread.php?t=314383")) but no joy.

---

### Post by a30d on 2007-09-04
This worked for me everyone... this post is from rob-acer and how to get the sound working again:

> Anyway, I found the fix at: [http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/](http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/).

I added two lines to the end of the alsa-base file using sudo gedit. This file is located in /etc/modprobe.d/alsa-base. Here are the two lines:

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3


Hope it works,
Bryan

---

### Post by Dave Crowhurst on 2007-09-04
Here is the output of /etc/modprobe.d/alsa-base

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto
options snd-hda-intel probe_mask=1
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

I added the two lines you suggested but still no sound :(

---

### Post by kikislater on 2007-09-12
Hello,

Sorry for my english I'm french !
I have a laptop acer aspire 5710zg like this : [http://www.topachat.com/pages/detail2_cat_est_micro_puis_rubrique_est_wport_puis_ref_est_inn653.html](http://www.topachat.com/pages/detail2_cat_est_micro_puis_rubrique_est_wport_puis_ref_est_inn653.html)

I haven't problem with sound. 
To make it work, you have to upgrade to kernel 2.6.20-16 or higher (with the kernel 2.6.20-15 it doesn't work)
Furthermore you have to compile the lastest alsa sound driver 1.0.15rc1 (The chipset is ALC268 We can see the change log on this link   [http://www.alsa-project.org/main/index.php/Changes_v1.0.15rc1_v1.0.15rc2](http://www.alsa-project.org/main/index.php/Changes_v1.0.15rc1_v1.0.15rc2)   
> Added the quirk entry for Casper CPR2000 (model=acer) with ALC268 codec 
    (ALSA bug#3343).)


Resume :
1.Upgrade your kernel,
apt-get install linux-image-2.6.20-16-generic
Restart your system with the new kernel

2.install the lastest alsa driver
install dependencies libncurses5-dev and build-essential
Download alsa-drivers , alsa-lib et alsa-utils
for the 3 packages you have to compile with :
./configure
make
make install

Therefor edit the /etc/modprobe.d/alsa-base with the line options snd-hda-intel model=acer
Run alsaconf to configure the sound

Restart and have fun :guitar:

---

### Post by Dave Crowhurst on 2007-09-16
Can you (or someone) please provide a very simple step-by-step guide for this fix. I have no idea what to do to get the sound to work as I have no prior experience with Linux.

---

### Post by Stegga on 2007-09-20
Did you get this fixed?
I have a fantastic laptop , with dolby everywhere and no sound!

I am, I guess as new as you to this, and don;t understand the way it is described here.

Please let me know if you found a solution to this.

Regards,
Andrew

---

### Post by kikislater on 2007-09-20
Sorry to be late !

Under Feisty run 

**First**
```

sudo apt-get install linux-image-2.6.20-16-generic
```
this fix upgrade your kernel
Restart your system

**Second : install dependencies**
```
sudo apt-get install build-essential libncurses5-dev
```

**Third : download the latest alsa driver :**
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc2.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc2.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2
```


**Fourth : install alsa driver :**
```
tar xjf alsa-driver-1.0.15rc2.tar.bz2
cd alsa-driver-1.0.15rc2
./configure
make
make install
```
```
tar xjf alsa-lib-1.0.15rc2.tar.bz2
cd alsa-lib-1.0.15rc2
./configure
make
make install
```
```
tar xjf alsa-utils-1.0.15rc1.tar.bz2
cd alsa-utils-1.0.15rc1
./configure
make
make install

```

[B]
Five : modifying options[/B]
Add ```
options snd-hda-intel model=acer
``` at the end of the file open with this command ```
sudo gedit /etc/modprobe.d/alsa-base
```
Save the file

**Final :**
Run alsaconf
Restart your system
Run alsamixer
Now you have sound !

See you

---

### Post by Dave Crowhurst on 2007-09-21
```
david@ubuntu:~$ tar xjf alsa-driver-1.0.15rc2.tar.bz2
david@ubuntu:~$ ./configure
bash: ./configure: No such file or directory

```

---

### Post by kikislater on 2007-09-23
Sorry,
tar xjf alsa-driver-1.0.15rc2.tar.bz2
cd alsa-driver-1.0.15rc2
./configure

The post is edited

Note : after each **make install** you have to make cd .. to return to the previous directory and you have to read a cup of the manual of ubuntu

---

### Post by Dave Crowhurst on 2007-10-14
Thanks for all the help everyone gave, but in the end I decided to give up on this machine and on Ubuntu. The laptop itself is a great bit of kit for running Windows, but it is just too much trouble to get Ubuntu to run on this a do anything useful.

---

### Post by kikislater on 2007-10-14
The laptop is running fine on ubuntu !
What kind of problem do you have?

---

