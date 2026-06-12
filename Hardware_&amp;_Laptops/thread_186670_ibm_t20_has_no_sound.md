---
title: "ibm t20 has no sound"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by broadlogic on 2006-06-02
i new to this. please walk me thru step by step to get the sound working. i see a sound icon and it has option of selecting device sound fusion cs46xx and cirrus logic cs4297a rev 4 but none of them produces any sound. thanks in adavnce. i have both the master and master mono volume at max

---

### Post by stimpsonjcat on 2006-06-02
check your PCM and ADC/DAC and unmute if necessary

---

### Post by broadlogic on 2006-06-02
thanks stimpsonjcat
checked PCM and ADC/DAC. these are not muted and at full volume.

---

### Post by jrei on 2006-06-03
Running Dapper on a T20 I didn't hat problems with the sound.

If you created a new user make sure he is in the 'audio ' group.

check with:
```

groups

```

if he is not use your main user which has sudo rights and do:
```

adduser audio

```

Another hint would be to turn of acpi. I had to do that to get suspend.
Todo so add the "acpi=off" to the kernel params in the '/boot/grub/menu.lst'.
Be aware to also add it to the "# defoptions=..." line.

Greetings, Jörn

---

### Post by jrei on 2006-06-03
please take a look at, 
[http://ubuntuforums.org/showthread.php?p=1085982#post1085982](http://ubuntuforums.org/showthread.php?p=1085982#post1085982)

---

### Post by broadlogic on 2006-06-04
jrei

i have audio right in groups and there are no other users.

here is the menu file

make change to turn acpi off and repost please. will try your advice but i am new to all this and do not want to make changes in case i corrupt the bootloader.

thanks

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by broadlogic on 2006-06-04
lets keep looking
sudo gedit /etc/modprobe.d/alsa-base

should this have a line to load sound fusion csxx drivers?

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

---

### Post by stimpsonjcat on 2006-06-04
hmmm. can you post the output of
```
sudo lspci
```
and
```
sudo lsmod | grep snd
```

---

### Post by odix on 2006-06-04
sorry for my simple sugestion, but I've a T22 and the reason why there was no sound was simply the three buttons (Volume+, Volume-, Mute) near the display. A simple klick on Volume+ solved my problem

regards
odi

---

### Post by broadlogic on 2006-06-17
[QUOTE=stimpsonjcat]hmmm. can you post the output of
```
sudo lspci
```
and
```
sudo lsmod | grep snd
```[/QUOTE]
sorry for not getting back earlier. i have not been able to boot into ubuntu. the video display does not come up. i can get to recovery mode and will have to figure that out prior to trouble shooting sound again

---

### Post by broadlogic on 2006-07-03
[QUOTE=odix]sorry for my simple sugestion, but I've a T22 and the reason why there was no sound was simply the three buttons (Volume+, Volume-, Mute) near the display. A simple klick on Volume+ solved my problem

regards
odi[/QUOTE]
this generate a screeching sound at max volume. at least there is some sound.

i found this on net about ibm thinkpad 600, and advice and relevance.


<<<<<<Problem description
There are two sound chips in these machines, a PCI based Crystal SoundFusion 4610, and an ISA based Crystal SoundFusion 4239. 

The Linux drivers for the CS4610 (both OSS and ALSA) expect to find it paired with an AC'97 codec chip, while instead the CS4610 is paired with the ISA CS4239. This was done, because at the time this allowed DOS games to output sound using SoundBlaster Pro emulation. 

To get sound under Linux you will have to use the OSS cs4232 or ALSA snd-cs4236 driver for the ISA soundchip instead. 

A good thread on the problem can be found in the alsa-devel mailing list 

[edit]Affected Models
ThinkPad 600E 
ThinkPad 770X, 770Z 
[edit]Solutions
[edit]Activating the devices
First you must make sure that the sound devices are activated. 

Disable "Quick Boot" in your ThinkPad BIOS, otherwise the sound devices will not be activated by the BIOS. To enter the BIOS, power cycle your ThinkPad and press F1 when the ThinkPad screen shows. 

You can also manually activate the sound card once booted: 

With apm and pnpbios, this is done with setpnp from the pcmcia package: 
# setpnp 0x0e on 
# setpnp 0x0f on 
With acpi and pnpacpi, use these commands: 
# echo 'activate' > /sys/devices/pnp0/00:05/resources 
# echo 'activate' > /sys/devices/pnp0/00:06/resources 
It seems that with very new kernels and ACPI enabled, you will need to manually enable the device even if you have correctly disabled "Quick Boot". 

This only works with newer kernels that fully support pnpacpi, and provided that this patch has been applied (applied to Linus' tree in july 2005). 

It seems that the default dma numbers change when pnpacpi is used (to dma1=1 dma2=3, for instance). 

If you're using acpi and pnpacpi, you can see which resources the sound card is using like this: 

# cat /sys/devices/pnp0/00:05/resources 
# cat /sys/devices/pnp0/00:06/resources 
[edit]Using ALSA
Compile the sound driver as a module and load it after everything else. You can add the following line to a boot script, ie. rc.local for that: 

/sbin/modprobe snd-cs4236 index=0 port=0x530 cport=0x538 irq=5 dma1=1 dma2=0 isapnp=0
This is reported to work at least with kernel 2.6.9, 2.6.13 and 2.6.15. 

There is a nice script which can do all this for you, including activation of the device and detecting the correct resource settings to use. 

[edit]Using OSS
Add the following lines to a boot script, ie. rc.local: 

modprobe sound
insmod ad1848
insmod uart401
insmod cs4232 io=0x530 irq=5 dma=1 dma2=0 
or try from commandline: 

modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=7 synthio=0x330 synthirq=7
In case an insmod or modprobe of cs4232 fails with the following error appearing at the console, via dmesg, or in /var/log/messages, double-check you have QUICKBOOT (in the BIOS) disabled. 

modprobe: FATAL: Error inserting cs4232: No such device
[edit]Audio loops
If your OSS module loads like it should, but audio loops or sounds choppy then reloading the module should help: 

# rmmod cs4232 && modprobe cs4232 
(For the modprobe command to work without IRQ/IO/DMA parameters, you'll probably want to add the correct parameters as an "options" clause in /etc/modprobe.conf)>>>>>>

---

### Post by broadlogic on 2006-07-03
output as requested. see my earlier post about ac codecs as a possible problem area
 [QUOTE=stimpsonjcat]hmmm. can you post the output of
```
sudo lspci
```
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)
0000:00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

and
```
sudo lsmod | grep snd
```[/QUOTE]
snd_cs46xx             85576  1
gameport               15496  2 snd_cs46xx
snd_rawmidi            25504  1 snd_cs46xx
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         92704  1 snd_cs46xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs46xx,snd_pcm

---

