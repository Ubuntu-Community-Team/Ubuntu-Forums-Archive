---
title: "M-Audio USB Quattro audio interface not working"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by 23meg on 2005-03-24
Hi,

My M-Audio USB Quattro audio interface is detected in device manager, but i don't see it listed anywhere as a selectable audio device (in volume control, for example, all i see listed is ALSA and OSS devices my laptop's internal sound chip). I eventually want to be able to use it as a full duplex 4-in 4-out audio interface for multitrack recording, but from what i've googled so far i reckon it will take serious work to get that done, so as a first step i'd like to be able to assign it to play the system sounds, output sound from xmms, xine etc.  :) 

any ideas? 

m.

---

### Post by 23meg on 2005-03-25
btw, i get the following output from the lsusb command:

Bus 003 Device 004: ID 045e:0053 Microsoft Corp.
Bus 003 Device 003: ID 059b:0177 Iomega Corp.
Bus 003 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0763:2001 Midiman
Bus 001 Device 001: ID 0000:0000

i have two usb 2.0 ports. a hub is plugged into one, into which my iomega external usb 2.0 drive and my m$ mouse plug. on the second port i have the quattro alone.

i don't have a /dev/dsp2 or even a /dev/dsp entry. the following items appear under /dev/snd: 

/dev/snd/timer
/dev/snd/pcmC1D1p
/dev/snd/pcmC1D1c
/dev/snd/pcmC1D0p
/dev/snd/pcmC1D0c
/dev/snd/pcmC0D1c
/dev/snd/pcmC0D0p
/dev/snd/pcmC0D0c
/dev/snd/midiC1D0
/dev/snd/controlC1
/dev/snd/controlC0

i think (part of) this is an alsa configuration issue.. (sigh)

---

### Post by 23meg on 2005-03-28
so, i somehow got the card working in xmms; two devices are listed, i think one for each pair of stereo outputs (the quattro has four independent outputs). the volume control doesn't work by default and i have to select "software volume control" in the alsa output plugin options. the problems at present are:

- i still don't get a mixer device for the card in gnome volume control
- i have no idea how to assign system sounds (startup, bell, etc) to the quattro instead of my laptop's internal sound chip

any help appreciated!

- meg

---

### Post by primeirocrime on 2005-03-29
hey I have the exact same device and I also have the same problems. Take a look here...I just found this out.

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=USB+Audio+Quattro.&chip=Cypress+AN2131XX&module=usb-audio](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Midiman%2FMAudio&card=USB+Audio+Quattro.&chip=Cypress+AN2131XX&module=usb-audio)

---

### Post by 23meg on 2005-03-29
thanks, i'll check that page out; here's some well compiled info i've found on how to get the quattro to work properly with Jack, which is my long-term goal.. it seems we need a patched kernel that allows realtime operations for that.

[http://wiki.linuxquestions.org/wiki/M-Audio_Quattro](http://wiki.linuxquestions.org/wiki/M-Audio_Quattro)

still no luck with mixer and system sounds.

m.

---

### Post by 23meg on 2005-04-06
anyone else having trouble with multiple audio devices where one device is a usb one? or any ideas on how to get a usb audio interface to show up in the mixer?

---

### Post by SFN on 2005-04-11
I just got a Tascam US-122 and it also does not show up in any mixer. It DOES show up in lsusb, when I plug it in:

xxxxx@xxxxx:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)
Bus 001 Device 001: ID 0000:0000
xxxxx@xxxxx:~$


I especially find this odd because the listing in lsusb will disappear and reappear as I unplug it or plug it in. So I know that my box knows it's there  but there is a light on the US-122 that lights up when a USB connection is made (at least it does in Windows - kills me to say that) and that never lights up in Ubuntu. 

Anyway, I'm continuing to search. I'll be sure and report anything I find.

---

### Post by mortram on 2005-04-13
Ubuntu 5.0.4 detected my Quattro automatically, but I wasn't able to get it to work until I disabled the on-board sound in BIOS, then Ubuntu switched to the Quattro as the main audio out.  

The sound has been grainy and stutters, but I haven't looked into fixing this yet because I still haven't been able to configure my modem!

---

### Post by 23meg on 2005-04-13
i have no way of disabling onboard sound from the bios.. how else can i tell Ubuntu not to initialize it at all and make the Quattro hw0 instead? or else, isn't there a simple way of choosing which device to use for system sounds?

---

### Post by SFN on 2005-04-24
OK. I've got the US-122 working. Here's how.

First, do

```
sudo apt-get install fxload
``` 

and download 

[http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb](http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb)

Then do

```
sudo dpkg -i alsa-tools_1.0.5-2_i386.deb
```

Now, /usr/share/doc/alsa-tools/README.Debian reveals:

"The alsa-tools packages is almost useles without the alsa-firmware one!

Awfully alsa-firmware has broken license terms and it's to legally
distributable at the moment. The AGNULA team is trying to solve the
issue."

There is a link there to the source for alsa-firmware but I downloaded an RPM from 

[http://rpm.pbone.net/index.php3/stat/4/idpl/1419735/com/alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1419735/com/alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm.html)

then did

```
sudo alien --to-deb alsa-firmware-1.0.6-1.cvs.rhfc2.ccrma.i386.rpm
``` 

and

```
sudo dpkg -i alsa-firmware_1.0.6-2_i386.deb
``` 

Once you have your deb installed (or got the install done from source) download [http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2](http://langerland.de/audio/usx2y/usx2y-fw-0.1b.tar.bz2) and extract it.

Do

```
lsusb
``` 

and make note of the bus and device. In this case:

Bus 001 Device 005: ID 1604:8005 Tascam US-224 Audio/Midi Controller

Now:

```
sudo fxload -s /path/to/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/001/005
``` 

The /001/005 comes from your lsusb results. 001 = Bus. 005 = Device

and

```
sudo usx2yloader 
``` 

Lights on US-122 come on

```
cat /proc/asound/cards
``` 

gives

0 [Live           ]: EMU10K1 - Sound Blaster Live!
                     Sound Blaster Live! (rev.10) at 0xd000, irq 18
1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                     TASCAM US-X2Y (1604:8007 if 0 at 001/006)


Upon reboot, the US-122 did not light up. Just do

```
sudo usx2yloader 
``` 

All is well.

I would imagine that the process for other devices are similar. 

Hope this helps.

---

### Post by SFN on 2005-04-24
UPDATE

I forgot a couple of things. I had already had alsa-tools and fxload installed. If you don't you'll need to do 

```
sudo apt-get install fxload
```

and download 

[http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb](http://ccrma.stanford.edu/mirrors/agnula/demudi-apt/pool/local/a/alsa-tools/alsa-tools_1.0.5-2_i386.deb)

Then do

```
sudo dpkg -i alsa-tools_1.0.5-2_i386.deb
```

I've updated my original instructions as well.

Last night I did all of this on my desktop. Today, I tried it on my notebook. All went well.

---

