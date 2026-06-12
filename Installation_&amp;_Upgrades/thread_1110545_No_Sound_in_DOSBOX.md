---
title: "No Sound in DOSBOX"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by JohnMorrow on 2009-03-29
Hello:

I have Hardy 8.04 installed on an HP Pavilion a1632x, which is an AMD 64 (Athlon X2) system. Both graphics and sound are on the motherboard (nVidia).

I installed DOSBOX and created the dosbox.conf file as described here:

[http://ubuntuforums.org/showthread.php?t=17197](http://ubuntuforums.org/showthread.php?t=17197)

I start Dosbox from Terminal and get these messages:

#START Terminal Session

john@HP-PAV-A1632:~$ dosbox
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
CONFIG:Loading primary settings from config file dosbox.conf
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss
john@HP-PAV-A1632:~$ 

#END Terminal Session

I have downloaded and extracted an old DOS game, Skyroads, which starts and runs normally, just no sound.

Sound works normally in all native linux apps (Rhythmbox, Mplayer, etc).

I assume I may need to edit dosbox.conf, but I don't know what to add or change.

Pertinent sections of dosbox.conf follow:

#START dosbox.conf extract

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
# mpu401      -- Type of MPU-401 to emulate: none, uart or intelligent.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device. In Windows put
#                the id of the device you want to use. See README for details.

mpu401=intelligent
device=default
config=

[sblaster]
# sbtype -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# sbbase,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the DOSBox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
#            All OPL modes are 'Adlib', except for CMS.
# oplrate -- Sample rate of OPL music emulation.

sbtype=sb16
sbbase=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

#END dosbox.conf extract

suggestions are appreciated, Thanks in Advance!

John

---

### Post by rohdef on 2009-04-10
I don't know if you found a solution, but if not try setting

rate=44100

that worked for me. Found the value using:

cat /proc/asound/card0/codec#0

---

