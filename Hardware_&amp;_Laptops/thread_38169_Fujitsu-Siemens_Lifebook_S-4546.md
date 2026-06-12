---
title: "Fujitsu-Siemens Lifebook S-4546"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by laserline on 2005-05-30
Hello - I own a Fujitsu-Siemens Lifebook S-4546 and have 2 issues:
The first is IRDA - I can't use it - I even don't know if it's installed.

The Second is SOUND - I have ALSA and ESD working in system sound, I can hear MP3 and watch video - but Sound in games doesn't work, I even set-up alsa and ESD in the game's settings and from the UBUNTU Multimeda selector...
(Alsa started working after using the Unofficial Ubuntu Guide tweak).

The laptop specs are here:
[http://www.antlinux.com/lifebook/](http://www.antlinux.com/lifebook/)

Thanks in advance,

Idan
Ubuntu 5.04

---

### Post by laserline on 2005-05-31
anyone ??

---

### Post by consecratus on 2005-06-01
Good day mate,

The IRDA is usually found in SYSTEM>ADMINISTRATION> DEVICE MANAGER

In the Device Manager you might see alot of bloody hardwares.
Now IRDA is usually in Port Connector 3rd Row(Most).

If you highlight individual port connectors it might say UNKNOWN in the Device tab on your right. But if you click on Advanced it shows what kind of details devices are inside your computer.

You also can find IRDA Utilities in universe side of Synaptics repo.
**irda-utils (0.9.16-8)**

If you are trying to beam IRDA with your phone, turn the IRDA in your phone and get close to as possible and something will happen..

As for your Sound.

Try these settings in your multimedia systems selector

Output: ESD
Input: OSS

I don't usually play games but just wondering, are you trying to play games via WINE? Or are you playing games on the Ubuntu's default games?
If you are playing default games try enabling the sound server in SYSTEM>PREFERENCE>SOUND

See how you go, mate

---

### Post by laserline on 2005-06-01
Thanks - will check at home and post my results.

Idan.

---

### Post by tranxene on 2005-06-10
hello laser,

me too, i got a s4546 :)

yes, install irda-utils from the universe-repository and then run
```
# dpkg-reconfigure irda-utils
```
as root and take care that you select the right port - in our case that's /dev/ttyS3

cheerz

tranxene

---

### Post by laserline on 2005-06-11
Thanks - I can see it works from tailing the kernel log...

I have  afew questions:
1. How did you know it was on /dev/ttyS3 ?
2. How do I use it for transfering files in and from a phone/PDA (palm T3) ?
3. How do I use it so my SonyEricsson T630 or any other phone will be a modem ?
4. Are there any programs that have a GUI with the IR utils?
5. In the BIOS of the S4546, is IR at your laptop IrDA or FIR ?

Thanks alot,

(hope these are not a lot of quistions  O:)  )

Idan

---

