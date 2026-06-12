---
title: "Assistance installing SB XtremeGamer soundcard..."
date: 2010-02-18
forum: Hardware
---

### Post by DefStatic on 2010-02-18
My first issue! Mark this day. This will certainly make or break my Linux experience.

[SIZE=2]**_Current Setup:_**[/SIZE]
**Monitor:** Samsung 24" 2494SW
**CPU:** AMD Opteron 165 
**MoBo:** BFG nForce4 Ultra Motherboard
**Memory:** 4 x 1GB Mushkin HP DDR400
**HDs:** 2x320GB Seagate SATAII in RAID0
**GPU:** PNY GeForce 9800GT PCI-Ex16
**Monitor:** Samsung 24" 2494SW
**SPU:** SB X-Fi xTremeGamer
**Speakers:** Klipsch Pro Media 2.1
**Media:** Sony DVD-RW SATA
**PSU:** Ultra X-Finity 600W PSU

Problem... Ubuntu 9.10 doesn't seem to acknowledge I have before mentioned soundcard.

Are these instructions still legit?

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

EDIT: Well, not giving up. I didn't for Vista. I can't imagine it can work in Vista but not Ubuntu. Also, if there is any information I am missing in my question that is delaying its ability to be answered please let me know.

---

### Post by DefStatic on 2010-02-18
Just an update, giving up on Google searches, moved to Bing, going to try a few things found there...

[http://www.linuxquestions.org/questions/ubuntu-63/cant-get-sound-card-to-work-with-ubuntu-762569/](http://www.linuxquestions.org/questions/ubuntu-63/cant-get-sound-card-to-work-with-ubuntu-762569/)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If I can't get this to work, do I put XtremeGamer (and therefor prob most Creative cards) on the Incompatibility List? Figures I would have a soundcard that Ubuntu doesn't have the ability to work with.

Also, don't know if this matters, but I installed Ubuntu from a pen drive live version made with [URL="http://www.google.com/url?sa=t&source=web&ct=res&cd=5&ved=0CB4QFjAE&url=http%3A%2F%2Funetbootin.sourceforge.net%2F&ei=-gl-S5SAM8KVtgeZ8ISoDw&usg=AFQjCNFG2iJy14ueI6PKA0HBkn1cP-KoBg"]UNetbootin.
[/URL]

---

### Post by DefStatic on 2010-02-18
Ok, well, one thing installed a lot of packages, but no sound. Not even a sound card showing up in my devices. At one point there were two, now there are none.

Going to try these things...

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)
[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

---

### Post by DefStatic on 2010-02-18
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB X-Fi
05:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

```Well, something is able to detect that there is a sound card... Interesting...

```
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 003: ID 046d:c318 Logitech, Inc. 
Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Strange... I guess the wireless adapter for the Performance MX is that Asahi thing. Oh well, doesnt really apply here.

```
# cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
```

and...

```
# cat /proc/asound/modules
cat: /proc/asound/modules: No such file or directory
```

That seems like it is going to be a problem... Any thoughts?

---

### Post by DefStatic on 2010-02-18
So I was going through some of this stuff... came to here...

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

And read...

> As of the writing of this message, the guide below is no longer needed  and should not be used. The reason being Alsa has finally produced a  working drive. Alsa's new drive is included in kernel 2.6.31.X. As of  Ubuntu 9.10 (Karmic Koala), the Creative X-Fi soundcard will work out of  the box!

WTF mate??? Mine did not work out of the box. However there were two cards listed before. Perhaps I screwed something up trying to fix all this???

---

### Post by DefStatic on 2010-02-19
So I put in the live USB version, and sure enough there was the card. No sound, but it was there.

So I formatted the drive and reinstalled, it found the card again, but no sound. Ran updates, and I had sound. A little pooping here and there, but I will look into that later.

Guess that's self service ;-) Thanks for the saved messages that had all the info!

---

