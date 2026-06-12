---
title: "Bluetooth headset only patially working  (ubuntu 12.04)"
date: 2012-05-06
forum: Hardware
---

### Post by Neill_R on 2012-05-06
**Blue-tooth headset only partially working  (Ubuntu 12.04)**

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 


I have a Nexus Talknano bluetooth headset. It  works fine with my Nokia 6300 phone and works in part with my computer.  It works, in that I can use the microphone with Skype and hear via the  sound card. However if i select the talknano for sound output nothing is  heard. However I can control the slider showing the output volume by  using the Talknano volume control buttons 

UBUNTU 12.04 on an ASROCK G31M-S motherboard.


When i get connect the talknano the following appears in seconds 

[COLOR=Red]ANY IDEAS PLEASE?[/COLOR]

Are the default settings in /etc/bluetooth/audio.conf correct?

lost to know what to look at next where is alsa config stored?

log viewer shows 

May  5 23:40:41 freds bluetoothd[879]: /org/bluez/879/hci0/dev_80_4C_04_00_1C_B2/fd14: fd(32) ready
May  5 23:40:41 freds rtkit-daemon[1517]: Successfully made thread 4279 of process 2532 (n/a) owned by '1000' RT at priority 5.
May  5 23:40:41 freds rtkit-daemon[1517]: Supervising 4 threads of 1 processes of 1 users.
May  5 23:40:46 freds bluetoothd[879]: Audio connection got disconnected
May  5 23:40:46 freds kernel: [ 6298.553042] Bluetooth: hci0 SCO packet for unknown connection handle 1
May  5 23:40:46 freds kernel: [ 6298.553053] Bluetooth: hci0 SCO packet for unknown connection handle 1
May  5 23:40:46 freds kernel: [ 6298.553059] Bluetooth: hci0 SCO packet for unknown connection handle 1



[COLOR=Red]details that might be of interest[/COLOR]

administrator@freds:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
administrator@freds:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA  Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 005: ID 0af0:6971 Option Globetrotter HSDPA Modem
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 007: ID 041e:406c Creative Technology, Ltd Live! Cam Sync [VF0520]
administrator@freds:~$ 


administrator@freds:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

administrator@freds:~$ sudo lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
administrator@freds:~$

administrator@freds:~$ sudo aplay -l
[sudo] password for administrator: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
administrator@freds:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.2.0-24-generic-pae/kernel/sound/firewire/snd-firewire-speakers.ko

administrator@freds:~$ sudo arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
administrator@freds:~$

---

### Post by musarraf172 on 2012-05-13
I am having similar issues with Dell Bluetooth headphone ! It will pair and connect but audio will not root throuh the headphone!!

---

### Post by Neill_R on 2012-05-17
we will have to wait till some clever person see this post...

---

### Post by tfc ken on 2012-05-24
Had the exact same problem with different model headset. Log out and log back in - but not into unity - switch your login session to GNOME. I know that's not the solution you want, but -"Ta-da" my headset now works in gnome. 

I've had innumerable problems with unity since upgrading to 12.04. I'm through with Unity.

---

### Post by Neill_R on 2012-07-07
Bump Anyone? Any ideas?

---

### Post by kedarlasane on 2012-07-07
I think you are used old bluetooth that are unknown to ubuntu API

---

### Post by Neill_R on 2012-07-10
Well I did do as you suggested and Ta-da it did not work. The only way i can use the bluetooth headset with skype is to have output audio to the built-in -audio analogue-stereo output mode and input from the talknano. But thanks anyway
<<<kedarlasane>>> Well the bluetooth dongle works fine with Nokia 6300 phone. I am using Ubuntu 12.04 that is up to date so thank  you also.

---

### Post by Drew1689 on 2012-07-27
I'm having a similar problem. I'm running Ubunutu 12.04 using a Plantronics Voyager Pro+. The audio works fine but I have no input options for the microphone. I was hoping to use it for presentation recording and Skype.

---

### Post by fullmoonguru on 2012-09-16
Check your settings in the Configuration tab of the Pulse Audio Volume Control Panel.  It needs to be set to Telephony Duplex and not High Fidelity Playback.

My problem is that it keeps dropping the connection when using Skype (Voyager Pro).

---

### Post by PJSingh5000 on 2013-01-27
I was able to get the Plantronics Voyager Pro Bluetooth USB microphone and earpiece working using PulseAudio Manager, as fullmoonguru suggested.

First, I installed PulseAudio Manager
```
$ sudo apt-get install paman
```


Then I confugured the Sound Settings and Pulse Audio as follows...


**Sound Settings** (launch from Unity taskbar)

_Output (tab):_
Select "Analog Output Plantronics BT300M"

_Input (tab):_
Analog Input Built-in Audio
(Note, Plantronics does not show up in the Sound Settings Applet).


**PulseAudio Volume Control** (launch from Unity dash)

_Playback (tab):_
Plantronics BT300M Analog Mono

_Recording (tab):_
Skype:  Plantronics BT300M Analog Mono
(Note, you must start an active Skype test call to see this option).

_Output Devices (tab):_
Built-in Audio Analog Stereo: Port: Analog Output, Lock, Not Selected
Plantronics BT300M Analog Mono: Port: Analog Output, Lock, Selected

_Input Devices (tab):_
Built-in Audio Analog Stereo: Port: Analog Input, Lock, Not Selected
Plantronics BT300M Analog Mono: Mono, Lock, Selected

_Configuration (tab):_
Built-in Audio: Analog Stereo Duplex
Plantronics BT300M: Analog Stereo Duplex
HD Webcam C525: Off
(Note, I had to disable the other micophone my system)

---

### Post by Neill_R on 2013-01-27
I am glad it works for your device but that does not help me with my talknano

---

