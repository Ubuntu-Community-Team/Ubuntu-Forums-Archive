---
title: "My wacom tablet doesn´t work in ubuntu 12.04"
date: 2012-05-05
forum: Hardware
---

### Post by Salvagluque on 2012-05-05
Hi guys,


Besides not being able to shut down my ubuntu system, (here´s the link to the tread [http://ubuntuforums.org/showthread.php?p=11908957#post11908957](http://ubuntuforums.org/showthread.php?p=11908957#post11908957), I´m also  struggling to make ubuntu 12.04 to recognize my wacom tablet, which I been serach high and low on the internet, but with no result. And I mean I looked like for months, tried every tut I could find, which at the time were for the ubuntu 11.10. I have install the grapic wacom tablet app for the management of the tablets and it keeps saying that it doesn´t find any. I also hava a wizardpen tablet, wich works perfectly fine.

the wacom tablet´s model is
ctl470l is a bamboo connect pen tablet.

Any ideas?

---

### Post by Favux on 2012-05-05
Hi Salvagluque,

The Bamboo Connect (Pen) isn't supported by Precise's 3.2 kernel.  It is by the 3.3 kernel.

So you need to update your wacom.ko, which is the Wacom kernel driver/module.

You need at least the version in input-wacom-0.12.1.  You could use Lekensteyn's PPA for that or compile 0.13.0 as in part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  A link to the PPA is just above part I.

---

### Post by Salvagluque on 2012-05-19
Thanks man.

this is the one that worked for me
[https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages](https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages)

just downloaded the deb package, installed it and restarted the machine.


Thanks.

---

### Post by Toporagno on 2012-05-21
> **Favux said:**
> Hi Salvagluque,

The Bamboo Connect (Pen) isn't supported by Precise's 3.2 kernel.  It is by the 3.3 kernel.

So you need to update your wacom.ko, which is the Wacom kernel driver/module.

You need at least the version in input-wacom-0.12.1.  You could use Lekensteyn's PPA for that or compile 0.13.0 as in part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  A link to the PPA is just above part I.
Hi Favux,
my wacom tablet isn't also recognized in ubuntu 12.04.
The model is (I think is a graphire) ET-0405-U.
Can you please tell me what I have to do?
Many thanks

---

### Post by Favux on 2012-05-21
Hi Toporagno,

That's an older model and should be supported.

Is it a usb Graphire?  Graphire 1 or 2 etc.?  What release of Ubuntu are you using?

Please run the following commands in a terminal and post the output:
```
lusb

xinput list

xsetwacom list
```

---

### Post by Toporagno on 2012-05-21
> **Favux said:**
> Hi Toporagno,

That's an older model and should be supported.

Is it a usb Graphire?  Graphire 1 or 2 etc.?  What release of Ubuntu are you using?

Please run the following commands in a terminal and post the output:
```
lusb

xinput list

xsetwacom list
```
Hi Favux first of all thanks for your reply.
It is a usb Graphire and I'm running Ubuntu 12.04.
Here the results of the commands:
```
marco@marco-Linux-Ubuntu:~$ lusb
No command 'lusb' found, did you mean:
 Command 'lush' from package 'lush' (universe)
 Command 'lsusb' from package 'usbutils' (main)
lusb: command not found
marco@marco-Linux-Ubuntu:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Philips SPZ2000                             id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
marco@marco-Linux-Ubuntu:~$ xsetwacom list
marco@marco-Linux-Ubuntu:~$ 

```

maybe you meant lsusb
```
marco@marco-Linux-Ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 004 Device 002: ID 0471:20d0 Philips (or NXP) 
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 003: ID 03f0:2005 Hewlett-Packard ScanJet 3570c
marco@marco-Linux-Ubuntu:~$ 

```

---

### Post by Favux on 2012-05-21
Those are with the Graphire plugged in?

We should be seeing something with the usb cable plugged in.  Does the tablet work in another OS or Distro or Ubuntu release?

Look for **wacom** in ***lsmod***.  Check that you have package xorg-xserver-input-wacom installed.

---

### Post by Toporagno on 2012-05-21
Yes the usb cable is plugged in and just to be sure I've also restarted the pc to make sure it was recognized. It works well in XP (Precise Pangoline is my first linux distro).
No entry for wacom in lsmod
```
marco@marco-Linux-Ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_usb_audio         101566  1 
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24603  1 snd_usb_audio
usbhid                 41906  0 
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
uvcvideo               67203  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
fglrx                2909855  114 
k10temp                12990  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  24 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_atk0110           17742  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
wmi                    18744  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
uas                    17699  0 
usb_storage            39646  1 
pata_atiixp            12999  0 
pata_marvell           12763  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56321  0 
marco@marco-Linux-Ubuntu:~$ 

```How do I check that I have the package xorg-xserver-input-wacom installed?
Sorry I'm totally new to linux :redface:

I think I've found the right command
```
marco@marco-Linux-Ubuntu:~$ dpkg -s xorg-xserver-input-wacom
Package `xorg-xserver-input-wacom' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

so I think I need to install it should I use apt-get?

---

### Post by Favux on 2012-05-21
> It works well in XP (Precise Pangoline is my first linux distro).
Alright that rules out a hardware problem.
> How do I check that I have the package xorg-xserver-input-wacom installed?
Open Software Center (the grocery bag on the taskbar) and search 'wacom' and click on the "show technical packages" at the bottom.  It should be installed by default.  So unless you did something it should be there.

But with:
> No entry for wacom in lsmod
we have likely found the problem.  The wacom.ko is the usb kernel module/driver needed for a usb connection to the tablet.  On some systems, for whatever reason, it does not auto-load like it should.

To fix that add 'wacom' (without the quotes) to the bottom of the modules file in /etc.  You could use:
```
gksudo gedit /etc/modules
```
Add 'wacom', Save, Close, and restart.

---

### Post by Toporagno on 2012-05-21
> Open Software Center (the grocery bag on the taskbar) and search 'wacom'  and click on the "show technical packages" at the bottom.  It should be  installed by default.  So unless you did something it should be there.
It say it's installed
> To fix that add 'wacom' (without the quotes) to the bottom of the modules file in /etc.  You could use:
     Code:
     gksudo gedit /etc/modules 
Add 'wacom', Save, Close, and restart.     Done but still no change

---

### Post by Favux on 2012-05-21
Is **wacom** now in ***lsmod***?  Sometimes restarting once or twice helps things shake out.

---

### Post by Toporagno on 2012-05-21
> **Favux said:**
> Is **wacom** now in ***lsmod***?  Sometimes restarting once or twice helps things shake out.
Yes **wacom** is in **lsmod** tried restarting a couple of times, even changed usb port but the tablet is still not recognized...

---

### Post by Favux on 2012-05-21
Alright, with the wacom module loaded anything now in ***lsusb*** or ***xinput list***?

Are other usb devices recognized by your system when you plug them in?

---

### Post by Toporagno on 2012-05-22
Hi Favux,
when I logged in this morning surprise surprise the tablet was there :guitar:
and everything works fine.

Many thanks man for your patience and for your help :KS

---

### Post by Favux on 2012-05-22
> when I logged in this morning surprise surprise the tablet was there
and everything works fine.

lol  The system just needed a good nights sleep.  :)

Glad to hear your Graphire is working.

---

### Post by riesengreen on 2012-10-30
Hi all and thanks as always.

Trying to make my Wacom Graphire Bluetooth work with Ubuntu 12.04 LTS. Each time I plug in the Bluetooth dongle and turn on the tablet, I get a "kernel oops".

Once I get it fixed, I don't think I'll ever move to another version! It just seems like a completely new puzzle each time I do.

Please see below for details, and if possible, let me know what I still might need to do. 

Thank you!

*The following have been installed using Synaptic Package Manager:
xserver-xorg-input-wacom
wacom-dkms
libwacom2
libwacom2-dbg
libwacom2-dev
libwacom-common
(Have not been able to find 'wacom-tools'. It doesn't exist anymore, if I am not mistaken.)

*Installed 'wacom-dkms_0.13.0-0ubuntu1~ppa1_all' (double-clicked, installed in Ubuntu Software Center)
from: 
[https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages](https://launchpad.net/~lekensteyn/+archive/wacom-tablet/+packages)
(Note: After I did this SpiderOak no longer launched at startup, and I could no longer open it. Removed and reinstalled, still can't open it.)

---

### Post by Favux on 2012-10-30
Hi riesengreen,

The first thing I would do is uninstall the dkms.  Lekensteyn's PPA installs input-wacom-0.13.0 and input-wacom is well past 0.14.0 currently.  A 0.15.0 is probably due out soon.

Besides it may not be the wacom.ko (usb kernel driver) from input-wacom that is the problem.  I would think you first want to investigate the Wacom bluetooth driver in the bluez stack.

So start with the Precise defaults.  The Wacom kernel drivers in Precise's 3.2 kernel and xf86-input-wacom-0.14.0.  As far as I know the bluetooth Graphire should work out of the box.

Did you also update xf86-input-wacom?

---

