---
title: "Thinkpad 600E"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by fazer on 2005-04-16
Are there any Thinkpad 600E users here?

If so, do you guys have the sound card and/or the modem working?

I am having huge trouble with both.  I can't seem to get the sound card working.

Here's my lsmod:
```

fazer@fazer:~$ lsmod
Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  4
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
snd_opl3_lib           10112  0
snd_hwdep               9220  1 snd_opl3_lib
snd_cs4236_lib         16000  0
snd_mpu401_uart         7168  0
snd_cs4231_lib         24832  1 snd_cs4236_lib
ipv6                  229504  9
af_packet              20744  2
ndiswrapper           119092  0
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
tsdev                   7488  0
usbhid                 29376  0
uhci_hcd               30224  0
usbcore               107384  4 ndiswrapper,usbhid,uhci_hcd
snd_cs46xx             80328  0
snd_rawmidi            22944  2 snd_mpu401_uart,snd_cs46xx
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_ac97_codec         64608  1 snd_cs46xx
snd_pcm                84872  4 snd_cs4236_lib,snd_cs4231_lib,snd_cs46xx,snd_ac97_codec
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50276  11 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_cs4231_lib,snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  3 snd_cs4231_lib,snd_cs46xx,snd_pcm


```


Here's my lspci:
```

fazer@fazer:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:06:00.0 Network controller: Broadcom Corporation: Unknown device 4325 (rev 02)


```

Any help would be **greatly** appreciated!

Thanks,

Fazer

---

### Post by sadneophite on 2005-04-16
This one worked for me today for the sound 

I removed /etc/modprobe.d/alsa-base
I then put the following file as alsa in the same directory


this is the alsa file at 

sudo /etc/modprobe.d/alsa
```

# Alsa 0.9.X kernel modules' configuration file.
# taken from http://linuxfocus.org/~guido/gentoo-tp600e/
#tp600e-gentoo1.4-config.html

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236 
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

```

Good luck

---

### Post by fazer on 2005-04-16
Hey, thanks for your help on IRC..


I think the reason why that didn't work for me is because after I go into the BIOS and do "initialize", I get a boot up error (not Linux) but IBM's BIOS starts yelling error 8611.  That's because my trackpoint has malfunctioned so I had to go into the CMOS and manually disable it.  

Can that be the reason why ?

Also, during boot up of Ubuntu, I get several beeps that seem to be executing the command `amixer` several times in a loop till like 10 times. After that, it just continues with the boot process.

I hope anyone out there who has used the IBM Thinkpad 600e can help me out.

Thanks.

---

### Post by fazer on 2005-04-17
[QUOTE=fazer]Hey, thanks for your help on IRC..


I think the reason why that didn't work for me is because after I go into the BIOS and do "initialize", I get a boot up error (not Linux) but IBM's BIOS starts yelling error 8611.  That's because my trackpoint has malfunctioned so I had to go into the CMOS and manually disable it.  

Can that be the reason why ?

Also, during boot up of Ubuntu, I get several beeps that seem to be executing the command `amixer` several times in a loop till like 10 times. After that, it just continues with the boot process.

I hope anyone out there who has used the IBM Thinkpad 600e can help me out.

Thanks.[/QUOTE]
 Hmm, it seems I was able to bypass those alsa errors upon boot up by doing what you mentioned above but replacing "cs4236" with "cs4232"  so, now I get the sound icon but no sound...damn it =(

---

### Post by sadneophite on 2005-04-18
If you got the sound icon, then it is working, you need to press fn + soundup key ... I think it was page up.  and you also have to put the mixer onto a higher setting.

The mixer icon means, according to my experience, that you HAVE SOUND YAY!!!

Good luck and have fun with sound.  yay 2.6 kernel.

---

### Post by viuks on 2005-04-23
[QUOTE=sadneophite]This one worked for me today for the sound 

I removed /etc/modprobe.d/alsa-base
I then put the following file as alsa in the same directory


this is the alsa file at 

sudo /etc/modprobe.d/alsa
```

# Alsa 0.9.X kernel modules' configuration file.
# taken from http://linuxfocus.org/~guido/gentoo-tp600e/
#tp600e-gentoo1.4-config.html

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236 
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

```

Good luck[/QUOTE]

YES! Thank You! I was trying to find it out about 3 months. Now it works. Gooood!

---

### Post by izak30 on 2005-09-22
Okay, i would really really like to stick with ubuntu (or even linux) but i still can't get this to work! i tried to copy and paste that code into /etc/modprobe.d/alsa, i get a couple of beeps on startus (badger release) and about 15 beeps in the hedgehog release.  it still says that the soundcard is not configured.  when i lspci i get this..

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
``` 

when i sudo modprobe snd-cs4236 
```
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.12-8-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
``` 

same with snd-cs4232 doesn't work

help please!   i was also wondering if anyone had any luck with ndis-wrapper and the thinkpad winmodem.

---

### Post by steigweis on 2005-10-23
i have the same problem! does anybody have an idea?
*bump*

---

### Post by rodzroom on 2007-08-22
> **sadneophite said:**
> This one worked for me today for the sound 

I removed /etc/modprobe.d/alsa-base
I then put the following file as alsa in the same directory


this is the alsa file at 

sudo /etc/modprobe.d/alsa
```

# Alsa 0.9.X kernel modules' configuration file.
# taken from http://linuxfocus.org/~guido/gentoo-tp600e/
#tp600e-gentoo1.4-config.html

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236 
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

```

Good luck

This is to confirm that this worked for me, too; Ubuntu 7.04 Feisty, with CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] as my sound card. It did not recognize that I had a sound card at all. I followed these instructions, then restarted my machine, and voila! Sound.

---

