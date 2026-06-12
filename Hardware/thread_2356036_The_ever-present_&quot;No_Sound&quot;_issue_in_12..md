---
title: "The ever-present &quot;No Sound&quot; issue in 12.04"
date: 2017-03-19
forum: Hardware
---

### Post by Darkness Falls on 2017-03-19
Hi there everyone.

My old laptop died the other week, and I've been installing 12.04 Precise Pangolin on my new one. There were teething issues with the sound on the old one, which were eventually fixed with the editing of /etc/modprobe.d/alsa-base.conf and everything went well for years. I even noted down the changes I made in case I had to do them again.

Thing is, of course, they're not working on the new one, and I don't know enough about the guts of Ubuntu to know what's gone wrong. My new laptop is an HP Envy 15 notebook with Bang and Olufsen Audio; it came with Windows 10, but I hate it, so I want to be able to move over to Ubuntu as soon as possible. So, here's the usual suspects:

```
df@df-HP-ENVY-Notebook:~$ uname -r
3.13.0-113-generic

```

```
df@df-HP-ENVY-Notebook:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 1904 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 1926 (rev 0a)
00:04.0 Signal processing controller: Intel Corporation Device 1903 (rev 09)
00:08.0 System peripheral: Intel Corporation Device 1911
00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21)
00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
00:15.0 Signal processing controller: Intel Corporation Device 9d60 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Device 9d61 (rev 21)
00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d12 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Device 9d14 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d48 (rev 21)
00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d70 (rev 21)
00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
01:00.0 Network controller: Intel Corporation Device 095a (rev 61)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 522a (rev 01)

```

```
df@df-HP-ENVY-Notebook:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ID 2008 Analog [ID 2008 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
df@df-HP-ENVY-Notebook:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ID 2008 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ID 2008 Analog
    Hardware device with all software conversions

```

I've tried uninstalling and reinstalling Pulseaudio and ALSA; I've installed ubuntu-restricted-extras; I've checked pavucontrol and alsamixer to make sure it's not muted. I've added
```
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel index=0 model=auto
options snd-hda-intel enable_msi=1


```
to /etc/modprobe.d/alsa-base.conf, and tried replacing model=auto with hp-m4, hp-dv5 and hp-hdx, none of which has worked. Gstreamer-properties tells me it's using ALSA, and it is pointing to ID 2008 Analog.

I'm not sure what else to try. Does anyone have any suggestions? Thanks in advance.

D.F.

---

### Post by Autodave on 2017-03-19
First off, what are the specs on your new machine?

Secondly, why are you installing an outdated version? You need to move up. 17.04 is the newest long term release: you probably need to get this on there first and then if there are still issues, someone here will be able to help you.  12.04 is done and gone: no more updates or security fixes anymore.

---

### Post by mörgæs on 2017-03-19
12.04 is strictly speaking still alive but only a month more.

17.04 is a short term support release due to be released in a month. You can try this one and 16.10 - if no big difference then go with the latter.

---

### Post by ajgreeny on 2017-03-19
Personally I suggest you try 16.04 which is the most recent LTS version and will be supported until 2021; if you install 16.10 it will be supported only until about July this year, and 17.04 when it is released, only until Feb 2018, both being short term support versions so having only 9 months each, then requiring an update.

Many, or perhaps most users, (there is no way to know for certain), but including me, use only the LTS versions and skip the intermediate ones, though I do always test the intermediate ones even before they are released as VMs in Virtualbox.

---

### Post by Perfect Storm on 2017-03-19
+1 for ubuntu 16.04 LTS. The chances that it support your sound-card is better.

---

### Post by Autodave on 2017-03-19
Typo on my end: it was supposed to be 16.04.  Sorry 'bout that.

---

### Post by mörgæs on 2017-03-19
> **Artificial Intelligence said:**
> The chances that it support your sound-card is better.

I would say chances are less.

The version with the best hardware support at any given time is always the development release, simply because it's where development takes place. Some day packages from this version might be backported to old releases like 16.04 but *if* it happens it does so with a big delay.

---

### Post by Darkness Falls on 2017-03-20
Hey everyone - thanks for the replies. I actually started out trying to  install 16.04 onto the laptop, but I couldn't get it to work; I have it  on a USB stick, but I clicked "try Ubuntu without installing" and it  never loads. It brings up the Ubuntu loading screen with the five lights  that turn from orange to white and back again, and then it hangs - the  lights stop changing colour, and it just stays like that forever.  Thinking maybe 16.04 wasn't compatible, I tried putting 14.04 on the  stick and trying again, with the same results. So 12.04 is the only  version that seems to work (plus I'm more familiar with it, since that's  the version I had on my old laptop).

As for system specs, I have:
```
-Computer-
Processor        : 4x Intel(R) Core(TM) i5-6260U CPU @ 1.80GHz
Memory        : 8062MB (1051MB used)
Operating System        : Ubuntu 12.04.5 LTS
User Name        : df (DF)
Date/Time        : Mon 20 Mar 2017 12:36:58 GMT
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Lid Switch
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Kensington      Kensington USB/PS2 Orbit
 HP Wireless hotkeys
 ST LIS3LV02DL Accelerometer
 HP WMI hotkeys
 SynPS/2 Synaptics TouchPad
 HDA Intel PCH Headphone
 HDA Intel PCH Mic
 HP Wide Vision HD
-Printers (CUPS)-
HP-LaserJet-2200        : <i>Default</i>
-SCSI Disks-
ATA WDC WD10SPCX-60K
ATA SanDisk SD8SNAT-
SanDisk Ultra

```
```
-Processors-
Intel(R) Core(TM) i5-6260U CPU @ 1.80GHz        : 1100.00MHz
Intel(R) Core(TM) i5-6260U CPU @ 1.80GHz        : 1700.00MHz
Intel(R) Core(TM) i5-6260U CPU @ 1.80GHz        : 400.00MHz
Intel(R) Core(TM) i5-6260U CPU @ 1.80GHz        : 600.00MHz

```
```
-PCI Devices-
Host bridge        : Intel Corporation Device 1904 (rev 09)
VGA compatible controller        : Intel Corporation Device 1926 (rev 0a) (prog-if 00 [VGA controller])
Signal processing controller        : Intel Corporation Device 1903 (rev 09)
System peripheral        : Intel Corporation Device 1911
USB controller        : Intel Corporation Device 9d2f (rev 21) (prog-if 30 [XHCI])
Signal processing controller        : Intel Corporation Device 9d31 (rev 21)
Signal processing controller        : Intel Corporation Device 9d60 (rev 21)
Signal processing controller        : Intel Corporation Device 9d61 (rev 21)
Communication controller        : Intel Corporation Device 9d3a (rev 21)
SATA controller        : Intel Corporation Device 9d03 (rev 21) (prog-if 01 [AHCI 1.0])
PCI bridge        : Intel Corporation Device 9d12 (rev f1) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation Device 9d14 (rev f1) (prog-if 00 [Normal decode])
ISA bridge        : Intel Corporation Device 9d48 (rev 21)
Memory controller        : Intel Corporation Device 9d21 (rev 21)
Audio device        : Intel Corporation Device 9d70 (rev 21)
SMBus        : Intel Corporation Device 9d23 (rev 21)
Network controller        : Intel Corporation Device 095a (rev 61)

```

The general consensus seems to be that I'd be better off trying to get 16.04 working rather than fiddling with 12.04; am I going to be better off abandoning attempts on this and working on 16.04?

D.F.

---

### Post by Darkness Falls on 2017-03-21
Long story short, you were all right - upgraded to 16.04 and the sound came back right on cue. Thanks everyone!

---

### Post by ajgreeny on 2017-03-21
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

