---
title: "turtle beach riviera PCI sound card"
date: 2008-11-02
forum: Hardware
---

### Post by mcskippy on 2008-11-02
ok I realize that ubuntu has some quirks.  especially with sound.  my onboard produces one side of stereo which I may be able to remedy through some jumper changes if this doesn't work.  I have had 2 turtle beach soundcards (santa cruz and riviera) that I have recently found out aren't supported in linux at all.  I purchased the most recent one (riviera) with the understanding (thanks new egg) that linux will find it in the PnP and all would be glorious.  oops.

so now I am faced with a driver install off the disk that is beyond me.  perhaps someone can walk me though it.  I will provide the read me text and maybe someone on here can make this process much less painful.  it has been a number of years since I was in a sun lab pounding out code in the wee hours of the mourning and I no longer program (and I am not sure I was ever good at it).  also I should add that ubuntu's security is stating that I am un-allowed to change certain files like the sound drivers as they are write protected.  I am trying to give myself ownership but I can't seem to get the right thing working in order to just get the ball rolling.

so here's what I have.  

cmpci-5.69.tar.gz

\\within that compressed file I have
cmpci 
cmpci.c                   \\C source code
config.in
configure.help
Makefile

the read me gives steps to build the driver but they aren't laid out for the layman.  so I will also post those.  again....I am a noob to ubuntu...
therefor I am not exactly command prompt oriented and havn't used a command prompt in probably 5 years.  so I need to know exactly what to type in to get results...these directions assume you know how to use your operating system (lol)! after reading all this I saw no reason that I couldn't do any of this using the GUI but it just wouldn't allow me access....I should also note that this read me says it's for several applications of linux such as redhat caldera and slackware, so I wasn't sure if the newer Ubuntu would operate similarly.  I appreciate any help I can get on the topic.  I needs me some sound I'm sick of it.  and I am so sick of windows I could use a vista box like an in flight barf bag on a turbulent flight and you got too partied out before the plane took off to vegas....I think some of you might know exactly what I mean...

STEPS TO BUILD DRIVER
================================================================================

  1. Backup the Config.in and Makefile in the sound driver directory
     (/usr/src/linux/driver/sound).
     The Configure.help provide help when you config driver in step
     4, please backup the original one (/usr/src/linux/Document) and
     copy this file.
     The cmpci is document for the driver in detail, please copy it
     to /usr/src/linux/Document/sound so you can refer it. Backup if
     there is already one.

  2. Extract the tar file by 'tar xvzf cmpci-xx.tar.gz' in the above
     directory.

  3. Change directory to /usr/src/linux

  4. Config cm8338 driver by 'make menuconfig', 'make config' or
     'make xconfig' command.

  5. Please select Sound Card (CONFIG_SOUND=m) support and CMPCI
     driver (CONFIG_SOUND_CMPCI=m) as modules. Resident mode not tested.
     For driver option, please refer 'DRIVER PARAMETER'

  6. Compile the kernel if necessary.

  7. Compile the modules by 'make modules'.

  8. Install the modules by 'make modules_install'


INSTALL DRIVER
================================================================================

  1. Before first time to run the driver, create module dependency by
     'depmod -a'

  2. To install the driver manually, enter 'modprobe cmpci'.

  3. Driver installation for various distributions:

    a. Slackware 4.0
       Add the 'modprobe cmpci' command in your /etc/rc.d/rc.modules
       file.so you can start the driver automatically each time booting.

    b. Caldera OpenLinux 2.2
       Use LISA to load the cmpci module.

    c. RedHat 6.0 and S.u.S.E. 6.1
       Add following command in /etc/conf.modules:

       alias sound cmpci

	also visit [http://www.cmedia.com.tw](http://www.cmedia.com.tw) for installation instruction.

DRIVER PARAMETER
================================================================================

  Some functions for the cm8738 can be configured in Kernel Configuration
  or modules parameters. Set these parameters to 1 to enable.

  mpu_io:	I/O ports base for MPU-401, 0 if disabled.
  fm_io:	I/O ports base for OPL-3, 0 if disabled.
  spdif_inverse:Inverse the S/PDIF-in signal, this depends on your
		CD-ROM or DVD-ROM.
  spdif_loop:   Enable S/PDIF loop, this route S/PDIF-in to S/PDIF-out
                directly.
  speakers:     Number of speakers used.
  use_line_as_rear:Enable this if you want to use line-in as
                rear-out.
  use_line_as_bass:Enable this if you want to use line-in as
                bass-out.
  modem:	You will need to set this parameter if you want to use
		the HSP modem. You need install the pctel.o, the modem
		driver itself.
  joystick:	Enable joystick. You will need to install Linux joystick
		driver.

---

### Post by jondiced on 2008-12-18
Hey mcskippy, I could really use some help with this too. I think I made it all the way through step 4 but I have no idea what to do after that. Hope someone comes around and explains it.

---

### Post by jondiced on 2008-12-18
Oh, I should also say that Riviera did work pretty well out of the box except for a few things, like Amarok doesn't produce sound anymore.

---

### Post by farna on 2010-01-21
Has anyone got one of these to wrok in Karmic? I'm using Mint 8 and have tried everything I can find. I bought the card because it was highly recommended for Linux Ubuntu. I tried removing pulse audio, no help. The computer knows the card is installed, and the motherboard sound is disabled. 

This seems to be my problem, but I'm too new to Linux to understand how to fix it:
swygert@Living-Room ~ $ aplay
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:608: audio open error: Device or resource busy

System Monitor doesn't show anything in Processes with "snd", "pcm", or "dmix" running. All commands to the sound card report that the resource is busy. 

This is an HTPC and has now become useless. I can revert to the motherboard sound, but then my surround sound is useless. Is my only choice to scrap Linux and install Windows XP?

---

### Post by Improviz on 2010-04-29
Anyone know if today's (4/29/2010) new release LTS version will fix the Turtle Beach issues? Or should I just spend $40 on a USB solution?

---

