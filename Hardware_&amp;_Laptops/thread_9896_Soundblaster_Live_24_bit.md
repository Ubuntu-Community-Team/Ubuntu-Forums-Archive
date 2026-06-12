---
title: "Soundblaster Live 24 bit"
date: 2005-01-02
forum: Hardware &amp; Laptops
---

### Post by fng on 2005-01-02
i have an onboard soundcard with my nforce 2 chip, but it didnt support hardware mixing.  So i bought myself a soundblaster live, because it is well supported by linux and has hardware mixing.

Well, it's a pain in the ass getting it running.

nforce 2 sound is disabled in the BIOS.

```
fng@butters:~ $ lspci | grep audio
0000:02:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
fng@butters:~ $
``` 

the soundcard is detected.

```
fng@butters:~ $ lsmod | grep emu10k1
fng@butters:~ $
```

No modules are loaded :/

```
fng@butters:~ $ sudo modprobe soundcore
fng@butters:~ $ sudo modprobe snd_emu10k1
fng@butters:~ $
```

both modules load without any errors.

```
fng@butters:~ $ sudo alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
fng@butters:~ $
``` 

Can't use the mixer-applet in gnome either.
Can anyone solve this?

---

### Post by fng on 2005-01-04
*bump*

anyone?

---

### Post by hardcandy on 2005-01-04
I believe the latest version Soundblaster Live 24-bit  is a different soundcard than SB 5.1 or older SBLive cards. I think what is happening is that this newest version has the same name and therefore when you go to ALSA.org and other sites it shows it as being supported. This latest version  has some software emulation for audio processing which is passed off to the CPU in Windows which is what is causing problems in Linux's driver. I know ALSA is working on a driver but it is still very alpha.  Any way of returning the card and exchanging it for a different model or brand? 
I bought one and tried for a week to get it to work without much success. I finally took it back and exchanged it for a Turtle Beach Santa Cruz.
This SB Live (the newest one) is it a very small card? That's what led me to believe it was using software emulation because it was only half the size of the other sound cards I looked at.

---

### Post by fng on 2005-01-04
yep, a very small card indeed.
Don't think there is a way of returning it :(
DAMN!

---

### Post by hardcandy on 2005-01-04
Use the onboard sound,.From What I read about this SBLivecard, the new one  uses the cpu to "hardware mix".
 [http://www.opensound.com/linux.html](http://www.opensound.com/linux.html) has a driver but it is $30 for the linux version. 
Anyway to add a hardware mixer as an external add-on, say use the output from the onboard sound and run it through a mixer? [http://www.soundonsound.com/sos/jun02/articles/mixercomputer.asp](http://www.soundonsound.com/sos/jun02/articles/mixercomputer.asp)

[http://www.zzounds.com/item--BEHUB802](http://www.zzounds.com/item--BEHUB802) $50 for a external mixer with nice features.

---

### Post by macewan on 2005-01-04
[QUOTE=hardcandy]Use the onboard sound,.From What I read about this SBLivecard, the new one  uses the cpu to "hardware mix".
 [http://www.opensound.com/linux.html](http://www.opensound.com/linux.html) has a driver but it is $30 for the linux version. 
Anyway to add a hardware mixer as an external add-on, say use the output from the onboard sound and run it through a mixer? [http://www.soundonsound.com/sos/jun02/articles/mixercomputer.asp](http://www.soundonsound.com/sos/jun02/articles/mixercomputer.asp)

[http://www.zzounds.com/item--BEHUB802](http://www.zzounds.com/item--BEHUB802) $50 for a external mixer with nice features.[/QUOTE]
 [http://alsa.opensrc.org/](http://alsa.opensrc.org/)

if you feel like reading

---

### Post by fng on 2005-01-06
I phoned the store yesterday.  They wont exchange it for another card. Not even if i offered to pay more.  Official response : "You opened the box, so we can't sell it anymore" Well DUH! How am I gonna test if the card works without opening the box?

After a big quest, i found someone to trade his old SB Live 5.1 for my new 1.  Gonna tried it this evenening

---

### Post by fng on 2005-01-06
An OLD SB Live! works perfectly!
Just putted into a PCI-slot and it worked out of the box. I even got HW mixing.
DAMN!

That new SB Live! is unworthy of the Live!-label! Dont buy it people!

---

