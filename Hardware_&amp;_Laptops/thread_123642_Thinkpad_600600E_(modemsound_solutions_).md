---
title: "Thinkpad 600/600E (modem/sound solutions ?)"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by kebajonathan on 2006-01-30
Ok, I have got some 600E I have to configure for some friends in Africa. So I'm trying to get my modem and sound to work. While doing this I found out PCMCIA didn't work. I don't know if this also applies to the 600 ? Anyway, this applies to the 600E, but it MAY apply to the 600 too. I cannot test it so please don't ask me. But if anyone here has suggestion for those who need it...

PCMCIA solution:
---------------------
Add the following options to you standard kernel line in /boot/grub/menu.lst:
              acpi=force pci=noacpi

Mwave modem solution:
-------------------------------
              1) get my binary deb (I don't know whether it works):
                              see attachment (I hope it works, otherwise use 2)
                              add the line "mwave" to /etc/modules to load on boot
              2) Compile the driver yourself:
                             A) download mwavem-2.0 from [http://sourceforge.net/projects/acpmodem](http://sourceforge.net/projects/acpmodem)
                              B) unpack and cd into it
                              C) with synaptic install make and gcc
                              D) ./configure
                              E) make
                              F) a) to build a bin package:
                                       sudo checkinstall -D make install
                                  b) to install without building a deb package:
                                        sudo make install
                              G) to load the driver on boot, add the followind line to /etc/modules:  mwave
                              H) Load the driver with "sudo modprobe mwave"
                               I)  Start System > Administration > Networking
                               J)  Open the properties dialog of the modem connection
                               K) You should know what to do here. The modem port is 
                                      /dev/mwave

Sound
--------
Ok, this is what I found ([http://www.ubuntuforums.org/showthread.php?t=94414](http://www.ubuntuforums.org/showthread.php?t=94414)) It works well with the 600E. To make you and overwiev I copy-paste it here:
           A) disable Quickboot in the BIOS (Press F1 to enter BIOS etup on boot)
           B) add these lines to /etc/modules:
                      sound
                      ad1848
                      uart401
                      snd-cs4236
           C) Follow these instructions:
1. Blacklist the incorrect sound card in /etc/hotplug/blacklist. Add lines for

snd-cs46xx
cs46xx

as written above - with the xx's

2. Add the following lines into /etc/modprobe.d/alsa-base

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

NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

3. Reboot.
(THX to grumpymole)

Now, my question:
-------------------------
The 600E's I have have to go to africa and the people there don't have a clue of PCs but they need to be able to connect to the Internet via MODEM in an easy way, without entering any commands or entering passwords. It should be graphically done. How can I best do this?

THX for answers
Jonathan

---

### Post by kebajonathan on 2006-01-30
For anyone who has already seen this. I edited the sound section. It works now on the 600E :D

---

### Post by gotaserena on 2006-02-01
install gnome-ppp and any user should be able to edit phone settings and such via GUI.

---

