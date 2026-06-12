---
title: "Laptop Sound Issue"
date: 2010-05-05
forum: Hardware
---

### Post by iavor on 2010-05-05
Hey guys,

I've had this problem on my previous Fedora 12 install and i tought the problem was the fedora itself.. but it wasnt so i booted Ubuntu 10.04 into Live Session.. now to the issue itself.

When i plug my headphones the sound of the speakers is supposed to stop and redirect to the headphones, but it wont stop and i can hear the speakers and the headphones working together. I've tried different headphones.. and the issue persists so headphones are not the problem. I im running Win7Home and i've listened music, whatched movies everything was fine. I really want to install Linux only on my lappy.

Here are the specs:
Core i5 M430
4GB DDR3 1333mhz
500GB 7200RPM i think it was Hitachi im not sure...
nVidia GT320M its basically a 9600M GT in disguise
audio card is intel_hda i believe ill post it later when i bootup windows to check out.

Thanks in advance.

EDIT: here is lspci

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a2d (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

i just got word from a friend who has the same issue and he have desktop computer not a lappy..

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by iavor on 2010-05-05
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

HP dv6 model "2166ss"

uname -a

> Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
 

aplay -l 

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/asound/version

> Advanced Linux Sound Architecture Driver Version 1.0.21.


head -n 1 /proc/asound/card*/codec#*

> ==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a


im going to install ubuntu on my external hard drive so that if i make any changes to be permanently

---

### Post by lidex on 2010-05-05
Dv6, huh? You sure that's your only audio issue? ALSA must be getting better. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by iavor on 2010-05-05
> **lidex said:**
> Dv6, huh? You sure that's your only audio issue? ALSA must be getting better. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

thank you m8 !!
this worked like a charm.. but i got this message: Ubuntu is running in low-graphics mode

---

### Post by iavor on 2010-05-05
i've reinstalled the vga drivers and so far seems ok

Much appreciated :)

---

### Post by lidex on 2010-05-05
You're welcome! If you would be so kind as to mark this thread as solved, I would appreciate that. Use 'Thread Tools' up top. I just looked at your sig :biggrin:

---

### Post by iavor on 2010-05-05
> **lidex said:**
> You're welcome! If you would be so kind as to mark this thread as solved, I would appreciate that. Use 'Thread Tools' up top. I just looked at your sig :biggrin:

Done! :) thanks again

EDIT: didnt saw any "rep" button or something similar is there any?

---

