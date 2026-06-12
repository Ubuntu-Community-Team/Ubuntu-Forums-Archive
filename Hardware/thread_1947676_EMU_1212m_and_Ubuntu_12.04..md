---
title: "EMU 1212m and Ubuntu 12.04."
date: 2012-03-27
forum: Hardware
---

### Post by DrPhuzzichtkeit on 2012-03-27
After spending 10.000 years on getting my soundcard working on 10.04 (mostly searching for information about how to enable it) I would like to write a small guide on how I just did it on 12.04.

[LIST=1]
[*]Add the [medibuntu repository]("https://help.ubuntu.com/community/Medibuntu").
[*]Install the alsa-firmware, i.e. in a terminal, run ```
sudo apt-get update && sudo apt-get install alsa-firmware
```.
[*]Restart the computer.
[*]In a terminal, run ```
alsa-mixer
```.
[*]Arrow left/right until you find <Clock In>.
[*]Arrow up/down to select 44100 (default is 48000).
[/LIST]
That's it!

Should probably work on 10.04 as well, but I can not confirm this as I mixed up my system there by double installing different alsa-firmware versions and so on...

---

### Post by DrPhuzzichtkeit on 2012-04-04
Just confirmed that this guide works on Ubuntu 10.04 as well.

---

### Post by lazarev on 2012-05-09
Great! Worked as a charm. Thanks a lot!

---

### Post by binloan on 2012-09-25
This is not working for me. I'm running Ubuntu 12.04 and I have the 1212m PCIe. I installed everything like said above. but when I try to start "alsamixer" it reports to me that there is not such file or directory. Also if I type in aplay -l get this:
> 
Karte 1: Generic [HD-Audio Generic], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

--> but for me it looks like the internal soundcard of my graphic card (amd radeon hd 5670)

when i type lspci -v I find this in the list:

> 
04:04.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
    Subsystem: Creative Labs Device 4007
    Flags: medium devsel, IRQ 16
    I/O ports at dc00 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel modules: snd-emu10k1


can anybody help me? Ubuntu without sound output is kinda... quiet ](*,)

---

### Post by M4st0d0n on 2012-10-07
Hello,

Bugs with PCIe versions of this card have been described here :

[http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m](http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m)

I've made my Emu1616m (1010m and microdock) work on Ubuntu TangoStudio (kernel 2.6.32-41-lowlatency) with manual compilation of the latest alsa version and a patch.

I've followed this how-to to compile alsa 1.0.25 with a script : [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

And applied the patch before compilation (point 6) on the freshly downloaded file named "emu10k1_main.c" somewhere in "/opt/". The patch can be found here on my post : [http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m&page=2](http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m&page=2)

Hope this will be of any help.

---

### Post by binloan on 2012-10-23
> **M4st0d0n said:**
> Hello,

Bugs with PCIe versions of this card have been described here :

[http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m](http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m)

I've made my Emu1616m (1010m and microdock) work on Ubuntu TangoStudio (kernel 2.6.32-41-lowlatency) with manual compilation of the latest alsa version and a patch.

I've followed this how-to to compile alsa 1.0.25 with a script : [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

And applied the patch before compilation (point 6) on the freshly downloaded file named "emu10k1_main.c" somewhere in "/opt/". The patch can be found here on my post : [http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m&page=2](http://ubuntuforums.org/showthread.php?t=1378290&highlight=emu+1616m&page=2)

Hope this will be of any help.

I changed the script (updated servers): [https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh](https://www.dropbox.com/s/qbsv955x248wm7s/AlsaUpgrade-1.0.25-3.sh)

Took this tut and followed the instructions of it: [http://ubuntuforums.org/showthread.php?t=1681577&page=20](http://ubuntuforums.org/showthread.php?t=1681577&page=20)

and then before compiling (step 6) patched the "emu10k1_main.c" in "opt/Alsa-1.0.25/alsa-driver7Alsa-kernel/pci/emu10k1/" like this:

> patch "your path"/pci/emu10k1/emu10k1_main.c /path/to/emu1010pcie.patch

then installed it like mentioned in the thread and after reboot I had working sound!

Great. Thanks.

---

### Post by drtechno on 2012-11-18
thanks I'm dumping my ubuntu and going to try the fedora distro since it supposed to work.

I'm not the rocket scientist like you guys, I do music for a living. And maybe you and make it do it automatically. 

plus this card needs to run at 176.4 khz. the s/mux system needs to work in both modes (x2 for 88.2/96 khz and x4 for 176.8/192khz ) for this card to work like it should.

maybe it has to do with the xilinx spartan chip don't know

---

### Post by JonnyRotten57 on 2013-07-17
Thanx Dr Phuzz!

Works perfectly. Know what you mean about 10k years.

Ubuntu Studio 13.04, Emu  1616m PCI. :D

---

