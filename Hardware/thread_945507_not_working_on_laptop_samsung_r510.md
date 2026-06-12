---
title: "not working on laptop samsung r510"
date: 2008-10-12
forum: Hardware
---

### Post by AGSzabo on 2008-10-12
i am out of answers, why is it not working on my laptop? during boot it just hangs. this is a part of what it says before hang:

```
wifi%d: unable to attach hardware: "hardware rewision not supported" (HAL status 13) 
```

---

### Post by overdrank on 2008-10-12
> **AGSzabo said:**
> i am out of answers, why is it not working on my laptop? during boot it just hangs. this is a part of what it says before hang:

```
wifi%d: unable to attach hardware: "hardware rewision not supported" (HAL status 13) 
```

Hi and I assume you are meaning Ubuntu is not installing? Could you give us some system specs and did you check the cd for errors?

---

### Post by AGSzabo on 2008-10-12
it was the booting from the life cd what did not work.

but it is strange: i tried again an now it works! in 8.10 even network and display resolution (1240x800) are what they should be (under 7.4 and 8.4 these did not work)! also usbstick and mp3player work now!

nevertheless i collected a lot of informations to my hardware under knoppix boots to the desktop (a lot of things dont work under knoppix).

```
root@Knoppix:/ramdisk/home/knoppix# lspci
00:00.0 Host bridge: Intel Corporation Unknown device 2a40 (rev 07)
00:01.0 PCI bridge: Intel Corporation Unknown device 2a41 (rev 07)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 03)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 03)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 03)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 03)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 03)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 03)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 03)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 03)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 03)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 03)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 03)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2919 (rev 03)
00:1f.2 SATA controller: Intel Corporation Unknown device 2929 (rev 03)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e8 (rev a1)
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
root@Knoppix:/ramdisk/home/knoppix#

root@Knoppix:/ramdisk/home/knoppix# lsusb
Bus 008 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 007 Device 002: ID 046d:c51b Logitech, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0ac8:c302 Z-Star Microelectronics Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
root@Knoppix:/ramdisk/home/knoppix#

(usbstick and mp3player are working , file exchange works)

root@Knoppix:/ramdisk/home/knoppix# lspcmcia
root@Knoppix:/ramdisk/home/knoppix#

(laptop does not have pcmcia
```

i guess i just have to install 8.10 and be lucky with it. but better i wait for the non-beta release?

---

### Post by AGSzabo on 2008-10-12
its weird. now for some reason it does not work again :( something "failed to execute /sbin/v86d" btw the cd is free of errors

---

### Post by AGSzabo on 2008-10-12
its even more weird because i tested again and now 8.10 beta works again! sometimes it does, sometimes not ...

---

### Post by fizyk on 2008-10-24
Got same problem for some time, but now it's fixed, 
Update to the latest kernel release (force update of ubuntu-desktop package through synaptic which will install missing packages) if you have to.
My only concern now is that currently I can't dim my screen, in any other way than through Nvidia X Server Settings pane.

---

### Post by IeU on 2008-12-06
I am also having problems,


tried the latest Xubuntu, it boots the cd, i choose to install Xubuntu (instead of loading LiveCD), it starts to load everything and i believe, once it tries to load the Kernel, the notebook restarts . . .


I have the: (It is very new, it is not even listed in Samsung Website)

> Samsung R510-Aura P7350 Damaris (NP-R510-FS09DE)

- Prozessor: **Intel**
- Prozessor Modell: **Intel Core 2 Duo**
- Prozessor Modellnummer: **P7350**
- Duo-Prozessor-Takt: **2 GHz**

- Arbeitsspeichersteckplätze: **2 x 2GB**
- Speichertyp: **DDR2**
- **4.096 MB** Speichergröße
- **800 MHz** Speichertaktung

- Northbridge-Chipsatz: **Intel PM45 Express**

- 15,40" Zoll großes Display
- Auflösung: 1.280 Pixel x 800 Pixel
- Grafikstandard: WXGA
- Displayeigenschaften: Glänzend

- 320 GB Festplattenkapazität
- Umdrehungsgeschwindigkeit 5.400 U/min

- Laufwerk: DVD-Super-Multi-DL-Brenner (Double Layer)
- Aufnahmemedien: CD-R, CD-RW, DVD+R, DVD+R DL, DVD+RW, DVD-R, DVD-R DL, DVD-RAM, DVD-RW

- Grafikkarte: NVidia Geforce 9200M GS
- 512 MB Grafikkartenspeicher
- 768 MB zusätzlicher Shared Memory

- Modem: 56k V.92
- LAN-Geschwindigkeit: 10 Mbit (IEEE 802.3), 100 Mbit (IEEE 802.3u), 1000 Mbit (IEEE 802.3ab)
- WLAN-Geschwindigkeit: 802.11b, 802.11g

- Eingebautes Mikrofon
- Webcam
- Eingebaute Lautsprecher

- Speicherkartenslot: SecureDigital Card
- 3x USB 2.0-Anschlüsse

- Anschlüsse: 15 Pin D-SUB Ausgang, DC-Eingang, Expresscard, Gigabit Ethernet RJ45 (1000 Mbit), HDMI-Ausgang, Kopfhörer, Mikrofon, USB 2.0

- Betriebssystem: Microsoft Windows Vista Home Premium

- Maße: B358 mm x H38,50 mm x T265,20 mm
- Gewicht 2,70 kg

---

### Post by AGSzabo on 2008-12-07
suddenly for me it just worked!

---

### Post by IeU on 2008-12-07
> **AGSzabo said:**
> suddenly for me it just worked!

Wireless working for you ?

---

### Post by AGSzabo on 2008-12-07
i dont know how to test this.

---

### Post by redmarten on 2008-12-10
> **IeU said:**
> Wireless working for you ?

Wireless is the only thing not working on my r510. Any ideas?

---

### Post by kickin on 2009-06-10
Hi, I'm having the same problem than you.... Don't know why. It begins when I've been trying to spoof nvidia driver in beta Seven 64 (build 7000) to make it recognise the card. Seems like the driver tried to modify the video card's bios.... Since then, I can't install any 64 bits system with the nvidia drivers....:( Any Idea to recover from this?

On Debian 64bits it reboots before install, on 9.04, it is while loading proprietary drivers.

> **IeU said:**
> I am also having problems,


tried the latest Xubuntu, it boots the cd, i choose to install Xubuntu (instead of loading LiveCD), it starts to load everything and i believe, once it tries to load the Kernel, the notebook restarts . . .


I have the: (It is very new, it is not even listed in Samsung Website)

---

### Post by AGSzabo on 2009-06-10
i dont know how, i dont know why but for me it must have been worked because i am using it right now :-) 

so its possible that for you it also might work somehow...

regards,
ags

---

### Post by kickin on 2009-06-10
I'll try again, but I was already able to install it, but could go after loading restricted drivers. Tried in rescue mode too, blacklist nvidia module too...

But I'll try again.

---

### Post by JohanoFiera on 2012-06-26
Hello,

I had the same/similar problems with the Samsung R510, model: NP-R510-FS0ANL. (The last 2 letters of the model only identify the country you bought it in, like DE/NL/etc. so it is actually a NP-R510-FS0A)

I tried all the option under F6, (ACPI = off, etc), I tried different versions like Ubuntu 11.10/12.04 CD and DVD versions, both amd64 and i386... but every time the laptop would reboot right after selecting "Install Ubuntu", or trying to boot the live CD of Ubuntu.

Now... I found the fix!

Simply download the BIOS Update from the samsung website and install it via a windows live CD, after that the Installation works with no more unexpected reboots :)

Hope this helps, enjoy!!

p.s. you can change the brightness control for the monitor in the BIOS from automatic to manual, in case you have issues with it ;)

---

