---
title: "Soundcard Santa Cruz not detected"
date: 2016-12-03
forum: Hardware
---

### Post by gcravelli on 2016-12-03
I installed Lubuntu 16.04.1 LTS on my Dell Dimension 8200, It is a dual boot with Windows XP.
There is a problem with the soundcard: 

gerard@XP8200:~$ lspci -v | grep -A7 -i "audio"
02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
    Subsystem: Voyetra Technologies Santa Cruz
    Flags: slow devsel, IRQ 16
    Memory at fe2ff000 (32-bit, non-prefetchable) [size=4K]
    Memory at fe100000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel modules: snd_cs46xx

I have run an 
!ALSA Information Script (v 0.4.64). The result is located at: 
[URL="http://www.alsa-project.org/db/?f=94afc651e4839092c7d3f459b5e39029b216a549"]http://www.alsa-project.org/db/?f=94afc651e4839092c7d3f459b5e39029b216a549

[/URL]
The soundcard is working under Windows XP and that is the only reason to keep Windows XP on my PC.
Please help.

---

### Post by Yellow Pasque on 2016-12-03
```
[   20.956574] snd_cs46xx 0000:02:07.0: Direct firmware load for cs46xx/cwc4630 failed with error -2
[   20.956594] snd_cs46xx 0000:02:07.0: firmware load error [cwc4630]
```

Ubuntu does not directly ship the firmware for your card (for legal reasons). The following commands should fix that:

```
cd ~/
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.29.tar.bz2
tar xjf alsa-firmware-1.0.29.tar.bz2
cd alsa-firmware-1.0.29/cs46xx/
sudo mkdir -p /lib/firmware/cs46xx
sudo install -m 644 ba1 cwc4630 cwcasync cwcbinhack cwcdma cwcsnoop /lib/firmware/cs46xx
```

Reboot the system.

---

### Post by gcravelli on 2016-12-03
Thanks Temujin,

Your advice helpt. The soundcards is now working. I had to raise the soundlevels in de alsamixer. 
The quality of the sound needs some more fine tuning. But most important: it works.


I have included a small portion of the Alsa info txt. (Icould not make an attachment of the whole file).


!Loaded ALSA modules
!!-------------------

snd_cs46xx


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfe2ff000/0xfe100000, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:07.0 0401: 1013:6003 (rev 01)
    Subsystem: 5053:3357

---

### Post by gcravelli on 2016-12-03
Thanks Temujin,

Your advice helpt. The soundcards is now working. I had to raise the soundlevels in de alsamixer. 
The quality of the sound needs some more fine tuning. But most important: it works.


I have included a small portion of the Alsa info txt. (Icould not make an attachment of the whole file).


!Loaded ALSA modules
!!-------------------

snd_cs46xx


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfe2ff000/0xfe100000, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:07.0 0401: 1013:6003 (rev 01)
    Subsystem: 5053:3357

---

### Post by gcravelli on 2016-12-03
Thanks Temujin,

Your advice helpt. The soundcards is now working. I had to raise the soundlevels in de alsamixer. 
The quality of the sound needs some more fine tuning. But most important: it works.


I have included a small portion of the Alsa info txt. (Icould not make an attachment of the whole file).


!Loaded ALSA modules
!!-------------------

snd_cs46xx


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfe2ff000/0xfe100000, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:07.0 0401: 1013:6003 (rev 01)
    Subsystem: 5053:3357

---

### Post by gcravelli on 2016-12-03
Thanks Temujin,

Your advice helpt. The soundcards is now working. I had to raise the soundlevels in de alsamixer. 
The quality of the sound needs some more fine tuning. But most important: it works.


I have included a small portion of the Alsa info txt. (I could not make an attachment of the whole file).


!Loaded ALSA modules
!!-------------------

snd_cs46xx


!!Sound Servers on this system
!!----------------------------

No sound servers found.


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfe2ff000/0xfe100000, irq 16


!!PCI Soundcards installed in the system
!!--------------------------------------

02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

02:07.0 0401: 1013:6003 (rev 01)
    Subsystem: 5053:3357

---

### Post by gcravelli on 2016-12-05
Before I asked Ubuntuforums for help, I have been messing around with my installation of Lubuntu. But I saw that the advice I received was working.
So I did a clean install of Lubuntu 16.04.1 LTS from the live CD and removed Windows XP completely.
After some fine-tuning in Alsamixer the sound is working fine (a bit louder would be nice). 
Thanks for the assistance.

---

### Post by tea for one on 2016-12-05
> **gcravelli said:**
> Before I asked Ubuntuforums for help, I have been messing around with my installation of Lubuntu. But I saw that the advice I received was working.
So I did a clean install of Lubuntu 16.04.1 LTS from the live CD and removed Windows XP completely.
After some fine-tuning in Alsamixer the sound is working fine (a bit louder would be nice). 
Thanks for the assistance.

Pulse audio is another package that controls sound and you can set it to output more than 100% if you wish.

I don't think that it comes automatically with Lubuntu but you can install it via the terminal or Synaptic

I notice that you previously had some sound problems so tread carefully. ;)

```
sudo apt install pavucontrol
```

---

