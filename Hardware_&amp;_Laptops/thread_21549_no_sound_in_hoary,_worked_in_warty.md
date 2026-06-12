---
title: "no sound in hoary, worked in warty"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by soulglo83 on 2005-03-22
initially my warty installation worked almost perfectly, after correcting an issue w/ ipv6 in firefox, setting up my printer and cdburner... i couldn't have been happier, so like a moron i upgraded to hoary. this being my first linux install i would like to find a way to get  the sound working w/o a new install (took me forever to get my system 100% to my liking).  ok enough background, here are details as to what i have and have tried
soundcard: ensoniq AudioPCI 5880, using es1371
ALSA, OSS, and the other one (ERS?) fail, ALSA appears to work but doesn't error out and doesn't actually provide any sound, OSS and the other option would tell me that they failed to form a pipeline.
i have unmuted Master in ALSAMixer and expiremented w/ muting other options (everytime i made sure the ic598(?) option was muted) 
#modprobe snd-ens1371

the contents of my lsmod are as follows (as i am unfamiliar w/ uploading attachments):

Module                  Size  Used by
proc_intf               4100  0 
freq_table              4100  0 
cpufreq_userspace       4572  0 
cpufreq_ondemand        6172  0 
cpufreq_powersave       1920  0 
radeon                 69760  1 
drm                    59412  2 radeon
video                  16260  0 
sony_acpi               6280  0 
pcc_acpi               11264  0 
button                  6800  0 
battery                10244  0 
container               4608  0 
ac                      4996  0 
8139cp                 19200  0 
8139too                24320  0 
mii                     4736  2 8139cp,8139too
snd_ens1371            22624  0 
snd_rawmidi            22944  1 snd_ens1371
snd_seq_device          8332  1 snd_rawmidi
gameport                4608  1 snd_ens1371
sis900                 18436  0 
snd_intel8x0m          17220  0 
snd_ac97_codec         64608  2 snd_ens1371,snd_intel8x0m
snd_pcm                84872  3 snd_ens1371,snd_intel8x0m,snd_ac97_codec
snd_timer              23300  1 snd_pcm
snd                    50276  7 snd_ens1371,snd_rawmidi,snd_seq_device,snd_intel8x0m,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0m,snd_pcm
usblp                  12032  0 
ohci_hcd               19848  0 
usbcore               107384  3 usblp,ohci_hcd
i2c_sis96x              5380  0 
i2c_sis630              7436  0 
i2c_core               21264  2 i2c_sis96x,i2c_sis630
shpchp                 86116  0 
pci_hotplug            30512  1 shpchp
sis_agp                 8068  1 
agpgart                31784  2 drm,sis_agp
parport_pc             34372  1 
md                     43856  0 
dm_mod                 53116  1 
capability              5000  0 
commoncap               7808  1 capability
lp                     10792  0 
parport                33480  2 parport_pc,lp
evdev                   9088  0 
tsdev                   7488  0 
ide_cd                 38532  0 
cdrom                  36508  1 ide_cd
mousedev               11160  1 
psmouse                19336  0 
ext3                  120968  2 
jbd                    54040  1 ext3
ide_generic             1664  0 
sis5513                15112  1 
ide_disk               18176  5 
ide_core              118988  4 ide_cd,ide_generic,sis5513,ide_disk
unix                   26164  580 
thermal                13576  0 
processor              22708  1 thermal
fan                     4612  0 
fbcon                  34048  0 
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

and of course my lspci:

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0d.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

I have also unmuted the volume in gnome's volume slidebar and sound's options.
I am relatively newbish, as this is my first linux install ever, but i have tackled the basics as far as google can take me. i have fathomed recompiling my ALSA drivers, but seeing as no one else seems to have this issue w/ ALSA 1.0.8 i figure im better off not creating more problems... Any help at all would be immenseley appreciated, and if I'm lacking any information that might be useful in diagnosing this, please let me know and I will post back ASAP. Thanks in advance.

EDIT: I had forgotten to mention how much I love ubuntu! Regardless, if my sound card works again or not, I will refuse to hand over my ubuntu partition to another OS, ever.

---

### Post by oracledarren on 2005-03-22
Hi

you said that you are newish to linux so i hope you understand this (dont me to appear patronising in anyway)  :) 

I notice from the list that you have an AC97 sound device so do the following

using synaptic install alsamixergui

open a terminal and type sudo alsamixergui and disable all of the digital outputs.

I think that it is really only IC958 output you need do

then come out of the mixer and type sudo alsactl store

Now your sound should be working fine  :)

---

### Post by telmo on 2005-03-22
That does not work! I have the same problem with the same soundcard, and when i open alsamixergui the values are not as i left them :(

Any suggestion?

---

### Post by soulglo83 on 2005-03-22
yes, oracledarren thank you so much! i had been very skeptical of your advice, i had done the exact same thing in alsamixer (like it had said in nearly all other forum responses) and it did no good, even with the alsactl store command. robert plant is currently able to assist me on my ubuntu journey, thanks to your help. apparently the alsamixergui did something altogether different on my system. oh and telmo, read oracledarren's response, the alsactl store command is the equivalent of clicking file and save inside alsa mixer, but its done from the cmd prompt after alsa's settings have been modified. if you dont run that command, when u reboot whatever settings u manipulated will return to default.

---

### Post by telmo on 2005-03-22
Thx. I'll try it again.

---

### Post by lynng on 2005-04-09
I had the same issue with a soundblaster pci card using the es1371 module.  I found that if I right clicked on the volune applet in the tray and went to Open Volume Control, then File->Change Device->Ensoniq Audio PCI (Alsamixer), the sound was immediately enabled.  Apparently it was using OSS mixer with the other device listed (SigmaTel-something) by default.  I only have one soundcard, so perhaps the other is the modem speaker?  I don't know, but now I have sound so I'm happy. \\:D/

---

### Post by Joh_ on 2005-04-09
I actually had the same problem with sound. The solution was to mute the channel named "IEC958 Capture Monitor" using alsamixer, then I had sound. :)

---

### Post by KiwiNZ on 2005-04-09
I have all but surrendered trying to get my sound working. I have nasty C-media Azalia onboard sound chip and it simply refuses to work.
I am so close to buying a card

---

### Post by telmo on 2005-04-09
I still have the same problem with my AC'97 card! :(
I want sound!!!!!  ](*,)

---

### Post by az on 2005-04-09
If sound worked in Warty, you can still just use the Warty kernel.  It will be supported for another 18 months.  Just make it your default in grub.

Using the newer kernel just because it is newer is not neccessary.

---

### Post by telmo on 2005-04-09
Howcome i didn't thought of that??? Heck, i feel DUMB!  :-#
I'll try it. Thank you!

---

### Post by telmo on 2005-04-10
errr.... now i remember... in Warty i used this same kernel from Hoary, that's what made the sound work... lol

Now what!?  ](*,)

---

### Post by bobterri on 2005-04-13
Hey, I have the same problem.  Sound worked in warty, not in hoary.  I have vt8233/A/8235/8237 AC97 Audio , on board sound too!  

When I tried to download alsamixergui in synaptic I couldn't find it.  Also, when I went to alsamixer in terminal, I did not have "IEC958 Capture Monitor" as an option to mute or unmute.

Anybody got any ideas?

---

### Post by telmo on 2005-04-13
[QUOTE=bobterri]Hey, I have the same problem.  Sound worked in warty, not in hoary.  I have vt8233/A/8235/8237 AC97 Audio , on board sound too!  

When I tried to download alsamixergui in synaptic I couldn't find it.  Also, when I went to alsamixer in terminal, I did not have "IEC958 Capture Monitor" as an option to mute or unmute.

Anybody got any ideas?[/QUOTE]

Yep! That thing is missing too in my alsamixer!  :?

---

### Post by XDevHald on 2005-04-13
From command type as root: 

**apt-get update**

**apt-get install alsamixergui**

if the package is there then type: **apt-get upgrade**

---

### Post by telmo on 2005-04-13
[QUOTE=Doc]From command type as root: 

**apt-get update**

**apt-get install alsamixergui**

if the package is there then type: **apt-get upgrade**[/QUOTE]

nop... the thing isnt the instalation of alsamixer, but the fact that "IEC958 Capture Monitor" isnt there...  :-?

---

### Post by bobterri on 2005-04-15
Exactly!

By the sticky in 5.04 hardware support forum, "Hoary Sound Broke?" maybe something major is wrong with 5.04!

I love everything about 5.04 except this.  I need sound, but it sounds like all kinds of people are having some problems with it.

---

### Post by jon_gunnar on 2005-04-16
[QUOTE=bobterri]Exactly!

By the sticky in 5.04 hardware support forum, "Hoary Sound Broke?" maybe something major is wrong with 5.04!

I love everything about 5.04 except this.  I need sound, but it sounds like all kinds of people are having some problems with it.[/QUOTE]

I got an onboard C-Media Electronics Inc CM8738 (rev 10)

and I have tried everything I can think of to get it working.
But no luck so far.  ](*,)

---

### Post by christooss on 2005-05-03
Have you tried this

[http://ubuntuforums.org/showthread.php?t=4253&highlight=cm8738](http://ubuntuforums.org/showthread.php?t=4253&highlight=cm8738)

---

### Post by ludi on 2005-05-03
[QUOTE=telmo]nop... the thing isnt the instalation of alsamixer, but the fact that "IEC958 Capture Monitor" isnt there...  :-?[/QUOTE]
Hi.
I have this chipset and the sound work with all option and everything else.
You can use kmix too.
Well, go to the terminal, type: alsamixer [enter], go to the right (press the right arrow key), you'll see the IC958.

---

