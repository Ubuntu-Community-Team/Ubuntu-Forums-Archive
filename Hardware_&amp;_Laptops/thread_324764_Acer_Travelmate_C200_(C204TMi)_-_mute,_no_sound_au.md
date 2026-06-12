---
title: "Acer Travelmate C200 (C204TMi) - mute, no sound audible, bluetooth switched off"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by MadeR on 2006-12-24
For Chirstmas I received a shiny new Acer Travelmate C204TMi.
[http://www.acer.it/acereuro/page4.do?sp=page3&dau22.oid=12900&UserCtxParam=0&GroupCtxParam=0&dctx1=11&CountryISOCtxParam=IT&LanguageISOCtxParam=it&ctx3=-1&ctx4=Italia&crc=717753816](http://www.acer.it/acereuro/page4.do?sp=page3&dau22.oid=12900&UserCtxParam=0&GroupCtxParam=0&dctx1=11&CountryISOCtxParam=IT&LanguageISOCtxParam=it&ctx3=-1&ctx4=Italia&crc=717753816)
[http://global.acer.com/products/tablet_pc/tmc200.htm](http://global.acer.com/products/tablet_pc/tmc200.htm)

I installed Kubuntu (Edgy Eft) and all work fine, even the stylus, but the sound part: and bluetooth.

the pc is mute, no sound can be heard from the embedded speaker, I tried also to install oss-alsa emulator.
It's a software issue because using Windows XP I can hear sounds.
The sound cartd is detected.
Both Kmix and alsamixer show that all volume sliders are set at 100%

and bluetooth indicator is switched off, but it works in XP.
[17179663.852000] Bluetooth: Core ver 2.8
[17179663.852000] NET: Registered protocol family 31
[17179663.852000] Bluetooth: HCI device and connection manager initialized
[17179663.852000] Bluetooth: HCI socket layer initialized
[17179664.028000] Bluetooth: L2CAP ver 2.8
[17179664.028000] Bluetooth: L2CAP socket layer initialized
[17179664.084000] Bluetooth: RFCOMM socket layer initialized
[17179664.084000] Bluetooth: RFCOMM TTY layer initialized
[17179664.084000] Bluetooth: RFCOMM ver 1.7



mader@mader-laptop:~$ sudo cat /dev/sndstat
Password:
Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux mader-laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xd000c000 irq 169

Audio devices:
0: ALC260 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC260







lspci:
mader@mader-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 6200 TurboCache (rev a1)
06:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
06:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller



what can I do?

---

### Post by MadeR on 2006-12-24
Solved: I installed the new alsa version: 1.0.14 release candidate 1 
[http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.14rc1.tar.bz2](http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.14rc1.tar.bz2)
the installation algorithm is easy!
launch a terminal and go to the directory where you've just downloaded the file.
expand it: 
```
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
```
move to the just created directory: 
```
cd alsa-driver-1.0.14rc1
```
make alsa detect your PC configuration: 
```
./configure
```
compile alsa: 
```
make
```
install alsa: 
```
sudo make install
```
remove the folder: 
```
cd ..; rm -rf alsa-driver-1.0.14rc1
```
modify the configuration file for kernel module loading according to your system: 
```
sudo vim /etc/modprobe.d/alsa-base
``` adding the line *options snd-hda-intel model=acer* 
Keep in mind that my PC is an Acer; you can find the list of snd-hda-intel module options in the  *alsa-driver-1.0.14rc1/alsa-kernel/pci/hda/patch_realtek.c* file and they are:
[list]
[li]basic[/li]
[li]hp[/li]
[li]hp_3013[/li]
[li]fujitsu_s702x[/li]
[li]acer[/li]
[li]test[/li]
[li]**auto**[/li]
[/list]
then reboot.

Using a mixer (alsamixer or kmix or the Ubuntu gnome one):
mute the microfone (your risk due to the feedback whistle to break your ears and the PC speakers) and move upwards the volume sliders.

Done! If it does not work, try all the possible options, rebooting after each change.

---

### Post by Takara on 2007-02-20
Hey there!

I got the same notebook last year and I searched for a solution for the sound for a long time.
Now I just did all the things, you mentioned and there is finally sound coming from my headphones ^^

But...
There is still no sound coming from the built in speakers :( 

Are yours working with these changes?

/edit
I just saw, that I only missed the sudo make install -.-

so its working now - thank you very much!!

---

### Post by MadeR on 2007-02-20
you are welcome :)

---

### Post by aspirina750 on 2007-04-25
> **MadeR said:**
> Solved: I installed the new alsa version: 1.0.14 release candidate 1 
[http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.14rc1.tar.bz2](http://www.alsa-project.org/alsa/ftp/driver/alsa-driver-1.0.14rc1.tar.bz2)
the installation algorithm is easy!
launch a terminal and go to the directory where you've just downloaded the file.
expand it: 
```
tar jxvf alsa-driver-1.0.14rc1.tar.bz2
```
move to the just created directory: 
```
cd alsa-driver-1.0.14rc1
```
make alsa detect your PC configuration: 
```
./configure
```
compile alsa: 
```
make
```
install alsa: 
```
sudo make install
```
remove the folder: 
```
cd ..; rm -rf alsa-driver-1.0.14rc1
```
modify the configuration file for kernel module loading according to your system: 
```
sudo vim /etc/modprobe.d/alsa-base
``` adding the line *options snd-hda-intel model=acer* 
Keep in mind that my PC is an Acer; you can find the list of snd-hda-intel module options in the  *alsa-driver-1.0.14rc1/alsa-kernel/pci/hda/patch_realtek.c* file and they are:
[list]
[li]basic[/li]
[li]hp[/li]
[li]hp_3013[/li]
[li]fujitsu_s702x[/li]
[li]acer[/li]
[li]test[/li]
[li]**auto**[/li]
[/list]
then reboot.

Using a mixer (alsamixer or kmix or the Ubuntu gnome one):
mute the microfone (your risk due to the feedback whistle to break your ears and the PC speakers) and move upwards the volume sliders.

Done! If it does not work, try all the possible options, rebooting after each change.


Hi there, I did all of the above using the rc3 and tried all the options, but I still have sound only from the headphones, any ideas?

BTW I also have a C200 (C202tmi)

Thanks!!!

BTW, I'm a newbie at this, so how do I check if it installed correctly?

P.S: I just saw that the alsamixer is showing version 1.0.13, is that correct? Thanks

---

### Post by MadeR on 2007-04-26
Is travelmate C202 endowed with the same sound card as C204?

---

### Post by aspirina750 on 2007-04-26
> **MadeR said:**
> Is travelmate C202 endowed with the same sound card as C204?

Yup, the Realtek ALC260 over a intel HDA

Weird thing is that I do all the steps, no error whatsoever, but I think it's still showing version .13
Any way I can confirm if it installed correctly?

Thanks

---

### Post by gigahz on 2007-05-22
> **Takara said:**
> I got the same notebook last year and I searched for a solution for the sound for a long time.
me too. Now I run Feisty, and it worked out of the box. Also the built-in speaker.

> There is still no sound coming from the built in speakers :( 
Did you turn up the master mono? Note also that when headphones are plugged in the internal speaker is disabled even if master mono is turned up. (at least here)

In my C200, I only have one speaker. The one to the right isn't one although it looks like it. So I would think master Mono is correct.

---

### Post by RanulfWolfSage on 2007-06-08
I have a HP dc5700 with a Realtek ALC260 HDA card running Ubuntu 7.04 Fiesty, I've tried the solution on this page but have a quick question. FYI, I'm a Linux n00b. In the alsa-base file, where should I put the string 'options snd-hda-intel model=<name>' ?

I added it to the end of the file, however there was an existing string that started the same way, 'options snd-cmipci mpu_port=0x330 fm_port=0x388'

I commented that out I believe, by putting a # sign at the front of it, but with it commented out or not, it still doesn't seem to give me sound. I verified that the mixer is not muted or turned down, and FWIW the built in mono PC speaker has worked this whole time, before and after updating alsa. I'd just like to get my stereo speakers working off the sound card. :(

Here's the file as it is now...

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
# options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=hp
```

Any suggestions, I would appreciate it, thanks!

PS. I installed the final release version, not the RC1 as it wouldn't install and the final release is newer anyway.

PSS. I un-commented out that line above what I added, and change the hp to hp_3013 and it worked! The only problem left though is that it's REALLY quiet. I have to crank both the headphones and PCM in alsa mixer to get it loud enough to hear without cranking the speakers. I guess for some reason it's linking them, and therefore making the output to the speakers quieter thinking headphones are attached? I had this problem with the driver for the card in XP. Although the driver allowed you to override the default and specify that it was not a headphone jack so the volume went up considerably. Any ideas?

---

### Post by Jadd on 2007-09-07
MadeR, thank you for that guide, it worked perfectly for me. I have the same soundcard but a packard bell laptop. Thanks for taking the trouble for writing that. You're one of the people that make the Ubuntu community so great. :)

---

