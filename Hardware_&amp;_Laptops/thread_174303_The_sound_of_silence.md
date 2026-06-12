---
title: "The sound of silence"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by jmpmjmpm on 2006-05-11
I have searhed high and low for a solution to my sound problem with Linux when running on my Packard Bell easynote a8202 laptop. I think the problem is with Linux not reconising the codec used in my Intel ICH6 on board sound device. I have looked through alsa bugtrack and although a bug has been submitted there seems to be no progress in fixing it.

My output of lspci is:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P
rocessor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM
L Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre
ss Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P
CI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil
y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                              y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                              y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR                                                              W (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97                                                               Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge                                                               (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family                                                              ) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus                                                               Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho                                                              st Controller
0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash                                                              Media Controller
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                                              /8139C+ (rev 10)

I bought this notebook in January and as it seemed to be a nice ultra portable, well it is, but I can't suffer in silence. This is the major problem that keeps my windows partition larger tahn my Kubuntu one!

If any of you guru's out there can help me fix this I would really appreciate it. (can I use oss instead of alsa?)

---

### Post by louis_nichols on 2006-05-11
What's the output of the command

```
lsmod | grep snd

```
We want to see if it loads any sound card modules at all.

---

### Post by jmpmjmpm on 2006-05-12
james@kubuntu-easynote:~$ lsmod | grep snd
snd_intel8x0           35932  3
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96644  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

hope this helps,

---

### Post by Kobalt on 2006-05-12
What version of Ubuntu do you curently use ?

---

### Post by ivansv on 2006-05-13
from personal experience linux laptops and sound dont work well with acpi enabled. do a "linux acpi=off" when installing or if installed find a way to turn acpi off.

---

### Post by louis_nichols on 2006-05-13
The loaded modules look ok to me... Did you try to see if you have sound for apps run as root? Just start your multimedia app with:

gksudo xmms

or an app of your choice. And then try to listen to music...

---

### Post by jmpmjmpm on 2006-05-13
I get this...

james@kubuntu-easynote:~$ gksudo xmms
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
sudo: xmms: command not found

so I try amarok instead, it start but seems with errors and there is still no sound. I get this...

james@kubuntu-easynote:~$ gksudo amarok
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kded: Launching previous backup analyse.
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
ScimInputContextPlugin()
amarok: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Warning: connect() failed: :

---

### Post by jmpmjmpm on 2006-05-13
[QUOTE=Kobalt]What version of Ubuntu do you curently use ?[/QUOTE]
dapper dake flight 7, I have had this problem always though, with hoary, breezy and dapper fl 4, 6 and 7. I   don't this will be fixed in the final release as I believe that the codec used in the connexant chip is not supported by alsa for whatever reason, but would love to be wrong!

---

### Post by jmpmjmpm on 2006-05-13
[QUOTE=ivansv]from personal experience linux laptops and sound dont work well with acpi enabled. do a "linux acpi=off" when installing or if installed find a way to turn acpi off.[/QUOTE]
I really do not want to turn acpi off on this notebook, I would loose too much functiiinality!

---

### Post by jmpmjmpm on 2006-05-13
I can remember reading somwhere that this issue was believed to be a confliccccct between the sound card and the modem. 

I am wondering if the connexant id31 chip that alsa is detecting is the modem chip and f there's a way to completely disable the modem so the sound chip would be detected if the is the case. I haven't heard of connexant making sound cards.

---

### Post by louis_nichols on 2006-05-13
well... your problem seems deeper than I thought. Look [here]("http://ubuntuforums.org/showthread.php?t=76019"). Follow the links in the thread(s) and see if anyone's found a solution yet.

---

### Post by jmpmjmpm on 2006-05-15
doesn't look like it...

c'mon ubuntu devs, sort it out plz

---

### Post by pompeyjohn on 2006-11-02
any news on this yet???

---

### Post by jmpmjmpm on 2007-01-05
please see my other thread for any updates I have, could a moderator please close this thread?

[http://www.ubuntuforums.org/showthread.php?t=136549&page=2](http://www.ubuntuforums.org/showthread.php?t=136549&page=2)

---

