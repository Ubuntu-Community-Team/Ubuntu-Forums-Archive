---
title: "I have a SB0510 module any drivers?"
date: 2021-05-20
forum: Hardware
---

### Post by devdlp on 2021-05-20
so i was first having trouble finding the drivers for my x-fi sound card.
Then it popped in my head? i should look for the module i have driver aswell.
Anyone out there have luck with this in ubuntu 21.04?
i still need the deb driver for the sound card aswell as the module the sound card is emu20k1, and the module is
SB0510....Thanks in adavance

---

### Post by Yellow Pasque on 2021-05-20
emu20k1 should be covered by the snd-ctxfi module. If that doesn't work, you're probably out of luck. Creative...
Also, can you upload the alsa info and copy the link?
```
sudo alsa-info
```

---

### Post by devdlp on 2021-05-21
sorry went right to sleep after work but here ya go.

[FONT=monospace][COLOR=#54ff54]**deven@deven-MS-7850**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo alsa-info [/COLOR]
[sudo] password for deven:  
ALSA Information Script v 0.4.64 
-------------------------------- 

This script visits the following commands/files to collect diagnostic 
information about your ALSA installation and sound related hardware. 

  dmesg 
  lspci 
  aplay 
  amixer 
  alsactl 
  /proc/asound/ 
  /sys/class/sound/ 
  ~/.asoundrc (etc.) 

See '/usr/sbin/alsa-info --help' for command line options. 

Newer version detected: 0.5.0 
To view the ChangeLog, please visit [http://www.alsa-project.org/alsa-info.sh.changelog](http://www.alsa-project.org/alsa-info.sh.changelog) 
The original file /usr/sbin/alsa-info will be overwritten! 
If you do not like to proceed, press Ctrl-C now.. 
ALSA-Info script has been updated. Please re-run it. 
[COLOR=#54ff54]**deven@deven-MS-7850**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]


[/FONT]

---

### Post by Yellow Pasque on 2021-05-21
"ALSA-Info script has been updated. Please re-run it."

Run it again:
```
sudo alsa-info
```

---

### Post by devdlp on 2021-05-22
[FONT=monospace][COLOR=#54ff54]**deven@deven-MS-7850**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo alsa-info [/COLOR]
[sudo] password for deven:  
ALSA Information Script v 0.5.0 
-------------------------------- 

This script visits the following commands/files to collect diagnostic 
information about your ALSA installation and sound related hardware. 

  dmesg 
  lspci 
  aplay 
  amixer 
  alsactl 
  rpm, dpkg 
  /proc/asound/ 
  /sys/class/sound/ 
  ~/.asoundrc (etc.) 

See '/usr/sbin/alsa-info --help' for command line options. 

/usr/sbin/alsa-info: line 661: tree: command not found 
/usr/sbin/alsa-info: line 661: tree: command not found 
/usr/sbin/alsa-info: line 661: tree: command not found 
/usr/sbin/alsa-info: line 661: tree: command not found 
/usr/sbin/alsa-info: line 661: tree: command not found 
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] :  
Your ALSA information is in /tmp/alsa-info.txt.LmbkaYHEVA


[/FONT]

---

### Post by devdlp on 2021-05-22
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 SB055x
 1 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf6914000 irq 35
 2 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf6910000 irq 36
 3 [Webcam         ]: USB-Audio - FULL HD 1080P Webcam
                      Generic FULL HD 1080P Webcam at usb-0000:00:14.0-3, high speed
 4 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf6080000 irq 17

---

### Post by devdlp on 2021-05-22
!!PCI Soundcards installed in the system
!!--------------------------------------

05:00.0 Multimedia audio controller [0401]: Creative Labs EMU20k1 [Sound Blaster X-Fi Series] [1102:0005]
    Subsystem: Creative Labs EMU20k1 [Sound Blaster X-Fi Series] [1102:002f]
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [1462:7850]
00:1b.0 Audio device [0403]: Intel Corporation 9 Series Chipset Family HD Audio Controller [8086:8ca0]
    Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family HD Audio Controller [1462:d850]
01:00.1 Audio device [0403]: NVIDIA Corporation GP106 High Definition Audio Controller [10de:10f1] (rev a1)
    Subsystem: PNY GP106 High Definition Audio Controller [196e:11d9]

---

### Post by Yellow Pasque on 2021-05-22
What exactly is the issue? Do you have no sound with the card or something else.

```
Automatically upload ALSA information to www.alsa-project.org? [y/N] :
```

You were supposed to say 'y' here, and copy/paste the link.

---

### Post by devdlp on 2021-05-22
[http://alsa-project.org/db/?f=265cbb336be10887e0ef130f846831863c822cd3](http://alsa-project.org/db/?f=265cbb336be10887e0ef130f846831863c822cd3)

---

### Post by devdlp on 2021-05-22
its a sb0510 module with a sb sound card and the module wont work in kubuntu but the sound card does

---

### Post by devdlp on 2021-05-23
i just dont know if there is a deb file driver for it so i can use it

---

### Post by Yellow Pasque on 2021-05-23
Wikipedia notes that the I/O Panel and IR remote are not supported by the snd-ctxfi driver because of lack of documentation/code from Creative: [https://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support](https://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support)

---

### Post by devdlp on 2021-05-24
dang, well thank you anyway

---

### Post by Yellow Pasque on 2021-05-24
> **devdlp said:**
> dang, well thank you anyway

You're welcome. I wish I could find a better source than Wikipedia to tell you that you're spinning your wheels. 
EDIT: Looking over snd-ctxfi changelog, it mostly looks like code cleanups of the original Creative code drop: [https://github.com/torvalds/linux/tree/master/sound/pci/ctxfi](https://github.com/torvalds/linux/tree/master/sound/pci/ctxfi)
Yeah, I think you're out of luck on this one :(

---

### Post by devdlp on 2021-05-24
yea its fine for now ill buy one thats more linux compatible

---

