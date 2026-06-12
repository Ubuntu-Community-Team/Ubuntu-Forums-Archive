---
title: "AAO D250 Sound/ Mic problem"
date: 2010-09-19
forum: Hardware
---

### Post by Blacklistx86 on 2010-09-19
Alright, I'm a little new to Ubuntu, and I was following a guide on the wiki on how to install the microphone drivers for the Acer Aspire One D250. Everything went smoothly until I rebooted and found out that the microphone doesn't work, and Now I have no sound! :(
```
xxx@xxx-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
xxx@xxx-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

```Any help?

---

### Post by lidex on 2010-09-19
Interesting. I've not seen "microphone drivers" previously. Do me a favor. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Blacklistx86 on 2010-09-20
Sorry for a delayed response!
[http://www.alsa-project.org/db/?f=13176344e6613af2f790d2dde3aff6bcc43a9263](http://www.alsa-project.org/db/?f=13176344e6613af2f790d2dde3aff6bcc43a9263)

---

### Post by lidex on 2010-09-21
Your alsa install is borked. Whatever you did, don't repeat it. Try re-installing. Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by lkjoel on 2010-09-25
> **Blacklistx86 said:**
> Alright, I'm a little new to Ubuntu, and I was following a guide on the wiki on how to install the microphone drivers for the Acer Aspire One D250. Everything went smoothly until I rebooted and found out that the microphone doesn't work, and Now I have no sound! :(
```
xxx@xxx-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
xxx@xxx-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

```Any help?
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by marisflowers on 2010-10-24
](*,)

I am completely new to Linux, and while this forum has walked me through some tough stuff, I am at the end of my rope with this sound problem! I have tried everything that is within my limited ability to do, and I must humbly beg for help...
I have an Acer Aspire One D250 running Ubuntu 10.4

[http://www.alsa-project.org/db/?f=7fef3e59db85fffbd599582ed1e82a88b7c310b8](http://www.alsa-project.org/db/?f=7fef3e59db85fffbd599582ed1e82a88b7c310b8)

Thank you so much to everyone who reads this - I appreciate your time!

](*,)

---

### Post by lidex on 2010-10-25
> **marisflowers said:**
> ](*,)

I am completely new to Linux, and while this forum has walked me through some tough stuff, I am at the end of my rope with this sound problem! I have tried everything that is within my limited ability to do, and I must humbly beg for help...
I have an Acer Aspire One D250 running Ubuntu 10.4

[http://www.alsa-project.org/db/?f=7fef3e59db85fffbd599582ed1e82a88b7c310b8](http://www.alsa-project.org/db/?f=7fef3e59db85fffbd599582ed1e82a88b7c310b8)

Thank you so much to everyone who reads this - I appreciate your time!

](*,)

First remove anything from alsa-base.conf that you added. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Remove any lines beginning with ```
snd-hda-intel
```Now save and close. Next re-install alsa.
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
When you're done with all that, I'll need to see where we are. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by marisflowers on 2010-10-26
Goodness - thank you for answering so quickly!

I think I did everything correctly, but I may have done so many things incorrectly it's too late.  

Please reply when you have time...my pathetic attempts at this must be at least good for a chuckle on your end!!

Have a great day, and thanks again for your expertise.

[http://www.alsa-project.org/db/?f=1597748e1dcf67bf76edc70fa3d87009fbe8ef16](http://www.alsa-project.org/db/?f=1597748e1dcf67bf76edc70fa3d87009fbe8ef16)

:redface:

---

### Post by lidex on 2010-10-26
> **marisflowers said:**
> Goodness - thank you for answering so quickly!

I think I did everything correctly, but I may have done so many things incorrectly it's too late.  

Please reply when you have time...my pathetic attempts at this must be at least good for a chuckle on your end!!

Have a great day, and thanks again for your expertise.

[http://www.alsa-project.org/db/?f=1597748e1dcf67bf76edc70fa3d87009fbe8ef16](http://www.alsa-project.org/db/?f=1597748e1dcf67bf76edc70fa3d87009fbe8ef16)

:redface:

Hmm. Can you post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```
also this:
```
dpkg -l | grep "alsa"
```

---

### Post by marisflowers on 2010-10-26
> **lidex said:**
> Hmm. Can you post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```also this:
```
dpkg -l | grep "alsa"
```

[COLOR=Green]Thank you for your speedy reply - I can't tell you how grateful I am for the help! 
Here is the information that you asked for:

[/COLOR]cat /etc/modprobe.d/alsa-base.conf[/CODE]:

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
options [COLOR=Red]snd[/COLOR]-[COLOR=Red]intel8x0m[/COLOR] index=-2 [COLOR=Red]I didn't delete this because there was no hda in the line...[/COLOR]
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


dpkg -l | grep "alsa":

rc  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
rc  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

[COLOR=Green]Please reply at your convenience - Muchísimas gracias y tienen un gran día!!![/COLOR]

---

### Post by lidex on 2010-10-26
Have you added some .conf files somewhere? Your alsa install is borked. Please re-install.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

### Post by marisflowers on 2010-10-28
> **lidex said:**
> Have you added some .conf files somewhere? Your alsa install is borked. Please re-install.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get purge linux-sound-base alsa-base alsa-utils

``````
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**


[COLOR=Green]I can't ever thank you enough for all of your help!  I did everything that you said and reinstalled alsa. It seemed like the installation went okay, but my soundcard isn't recognized...could that be the root of this whole thing? Like I said, I'm such a noobie to all of this. I feel bad taking up so much of your time - although I really do appreciate everything you've helped me with. This will be my last stab at this sound thing...if you have time (at your convenience!) to point me in the right direction I would be very grateful.
If you're sick of this whole thing, I totally understand. You've been so great and I can't thank you enough![/COLOR]

                                            -laptop:~$ aplay -l 
aplay: device_list:223: no soundcards found...
                                            -laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 56280000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 50f0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 56300000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0
    Memory at 56200000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 56340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 55100000-561fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 54100000-550fffff
    Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00002fff
    Memory behind bridge: 53000000-540fffff
    Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 50a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 5080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 56344400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 50c0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
    I/O ports at 50d8 [size=8]
    I/O ports at 50fc [size=4]
    I/O ports at 50d0 [size=8]
    I/O ports at 50f8 [size=4]
    I/O ports at 5020 [size=16]
    Memory at 56344000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: medium devsel, IRQ 11
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e00d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 55100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

03:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at 53000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 1000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

---

### Post by lidex on 2010-10-28
Can you run the alsa-info script again please?

---

### Post by marisflowers on 2010-10-28
> **lidex said:**
> Can you run the alsa-info script again please?


Many, many karmic blessings for still wanting to help!!! Here is the information that you requested:


  [http://www.alsa-project.org/db/?f=f877743fe68eb2edeba64db862b3c30a83e68a82](http://www.alsa-project.org/db/?f=f877743fe68eb2edeba64db862b3c30a83e68a82)

Thank you again -Hare Hare!!!!!!

---

### Post by lidex on 2010-11-03
Sorry if I lost you. Please remove any alsa-backports you may have installed and re-install alsa using the commands from earlier in this thread.

---

