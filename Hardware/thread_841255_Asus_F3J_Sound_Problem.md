---
title: "Asus F3J Sound Problem"
date: 2008-06-26
forum: Hardware
---

### Post by richyl2006 on 2008-06-26
Hi, real newb to ubuntu. Been looking around forums and seen couple of sound issues but non seem to relate to mine, hence this thread.

My laptop is an Asus F3J running Ubunutu 8 and the speakers work, and so do the headphones, but the problem is they work simultaneously. 

Need help because i don't want to have to revert back to windows (Gasp!).

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> Hi, real newb to ubuntu. Been looking around forums and seen couple of sound issues but non seem to relate to mine, hence this thread.

My laptop is an Asus F3J running Ubunutu 8 and the speakers work, and so do the headphones, but the problem is they work simultaneously. 

Need help because i don't want to have to revert back to windows (Gasp!).

EDIT
Do you mean your speakers work with even headphones are plugged in ?

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> Do you mean they don't work if headphones are not plugged in or vice-versa?

Wow quick reply, thanks! The speakers work when the headphones are plugged in.

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> Wow quick reply, thanks! The speakers work when the headphones are plugged in.

just to clarify, does that mean speakers don't work without headphones?

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> just to clarify, does that mean speakers don't work without headphones?

No the speakers on the laptop work fine. But when i plug in the headphones, they continue to work (i can hear sound in the headphones but it is not cutting off the speakers).

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> No the speakers on the laptop work fine. But when i plug in the headphones, they continue to work (i can hear sound in the headphones but it is not cutting off the speakers).

can you post output of the follwoing:

```
lspci
```

```
aplay-l
```

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> can you post output of the follwoing:

```
lspci
```

```
aplay-l
```

**lspci**

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

**aplay-l**

command not found

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> **lspci**

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

**aplay-l**

command not found

soryy it is ```
aplay -l 
```typo

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> soryy it is ```
aplay -l 
```typo

**aplay -1**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ukripper on 2008-06-26
soemone else has problem with this chipset to make it work properly.

here is the link how they done it - [http://ubuntuforums.org/showthread.php?p=4869649](http://ubuntuforums.org/showthread.php?p=4869649)

follow instructions and you will be ok!


Quotes taken from there :

"OMG ITS WORKING! the laptop speakers are completely off and only headphones work which is AWESOME. laptop speakers suck anyway.

now i gotta find out what fixed it lol so i can post here if anyone else has the same problem


ok i think the fix was a combination of these two:

adding "options snd-hda-intel model=3stack-dig" in # gksu gedit /etc/modprobe.d/alsa-base
AND

i added this [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf)
to sudo ./alsaconf.sh then save
then chmod it and ran it.
it did something
then restart and it worked "

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> soemone else has problem with this chipset to make it work properly.

here is the link how they done it - [http://ubuntuforums.org/showthread.php?p=4869649](http://ubuntuforums.org/showthread.php?p=4869649)

follow instructions and you will be ok!


Quotes taken from there :

"OMG ITS WORKING! the laptop speakers are completely off and only headphones work which is AWESOME. laptop speakers suck anyway.

now i gotta find out what fixed it lol so i can post here if anyone else has the same problem


ok i think the fix was a combination of these two:

adding "options snd-hda-intel model=3stack-dig" in # gksu gedit /etc/modprobe.d/alsa-base
AND

i added this [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf)
to sudo ./alsaconf.sh then save
then chmod it and ran it.
it did something
then restart and it worked "

thanks for the quick and excellent replies, many thanks!!

i just add options snd-hda-intel model=3stack-dig to the bottom of the alsa-base thingy yeh? or is there a certain place it should go?

---

### Post by ukripper on 2008-06-26
Personally, I would do only this and try:
 
```
gksu gedit /etc/modprobe.d/alsa-base
```

and add this to the bottom of the file
> options snd-hda-intel model=3stack-dig

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> Personally, I would do only this and try:
 
```
gksu gedit /etc/modprobe.d/alsa-base
```

and add this to the bottom of the file

Done that. Do i need to restart the computer to see if it works?

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> Done that. Do i need to restart the computer to see if it works?

yeh preferably restart.

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> Personally, I would do only this and try:
 
```
gksu gedit /etc/modprobe.d/alsa-base
```

and add this to the bottom of the file

Didn't work. Sound still coming out of speakers.

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> Didn't work. Sound still coming out of speakers.

ok delete the previous entry and use this instead:
> options snd-hda-intel probe_mask=1 model=3stack

in /etc/modprobe.d/alsa-base.

and then restart.

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> ok delete the previous entry and use this instead:


in /etc/modprobe.d/alsa-base.

and then restart.

Nope, didn't work :(

---

### Post by ukripper on 2008-06-26
try replacing with this:
> options snd-hda-intel position_fix=1 model=3stack

save and restart

---

### Post by chunchengch on 2008-06-26
I have Ubuntu 8.04 on my ASUS F3Jc laptop, sound works normally except the mic, here is my /etc/modprobe.d/alsa-base for your reference, maybe you can backup yours first and then replace it with mine to see if the problem is solved, be sure to save and reboot, good luck!


[COLOR="Green"]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/COLOR]

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> try replacing with this:


save and restart

Tried, did not work :(

---

### Post by richyl2006 on 2008-06-26
> **chunchengch said:**
> I have Ubuntu 8.04 on my ASUS F3Jc laptop, sound works normally except the mic, here is my /etc/modprobe.d/alsa-base for your reference, maybe you can backup yours first and then replace it with mine to see if the problem is solved, be sure to save and reboot, good luck!


[COLOR="Green"]# autoloader aliases
i...
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/COLOR]

Will try this, thanks for the help guys!

---

### Post by richyl2006 on 2008-06-26
> **chunchengch said:**
> I have Ubuntu 8.04 on my ASUS F3Jc laptop, sound works normally except the mic, here is my /etc/modprobe.d/alsa-base for your reference, maybe you can backup yours first and then replace it with mine to see if the problem is solved, be sure to save and reboot, good luck!


[COLOR="Green"]# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388[/COLOR]

Didn't work either :(

---

### Post by ukripper on 2008-06-26
> **richyl2006 said:**
> Didn't work either :(

Can you post screenshot after putting below command in terminal:
```
alsamixer
```

---

### Post by ukripper on 2008-06-26
We have tried almost all options. i suggest you should try using the latest drivers which is 17-rc2 on alsa project and see if that fixes your issues.

Excellent guide is here just follow this .. i never had any problem using this guide since feisty days - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> Can you post screenshot after putting below command in terminal:
```
alsamixer
```

DOn't know how to post screenshots so i just copied it below.

[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC660-VD                                                      &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-46.00]                                                &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     28              100<>100 100<>100  68<>68     0<>0    71<>71   81<>81    &#9474;
&#9474; < Master >Headphon    PCM     Front   Front Mi  Front Mi   Line      CD

---

### Post by ukripper on 2008-06-26
When you on headphones if you do FRONT SPEAKERS mute does it effect on your headphones too?

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> When you on headphones if you do FRONT SPEAKERS mute does it effect on your headphones too?

On my volume control i have controls on the following:

Master PCM  Front  Front Mic   Line in     CD     PC Speaker

When i move PCM and/or front it controls the sound on both the speakers and the headphones.

I.e. speaker control seems to be affecting the speaker and headphone volume at the same time.

---

### Post by ukripper on 2008-06-26
> **ukripper said:**
> We have tried almost all options. i suggest you should try using the latest drivers which is 17-rc2 on alsa project and see if that fixes your issues.

Excellent guide is here just follow this .. i never had any problem using this guide since feisty days - [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Then i would suggest follow this post and see if new drivers 17rc2 fixes this for you meanwhile i ll try to work it out or do a search.

---

### Post by richyl2006 on 2008-06-26
> **ukripper said:**
> Then i would suggest follow this post and see if new drivers 17rc2 fixes this for you meanwhile i ll try to work it out or do a search.

Many thanks!

---

