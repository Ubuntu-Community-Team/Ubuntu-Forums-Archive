---
title: "No sound, need help."
date: 2009-02-04
forum: Hardware
---

### Post by GARoss on 2009-02-04
I'm a newby needing help.
Apparently, Ubuntu 8.10 saw my MB's audio when I 1st installed. I turned off MB device in BIOS & Ubuntu now recognizes my Creative Audigy 2 sound card but I still get no sound. 
I found a help site, [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting), which had me open a terminal & type "find /lib/modules/`uname -r` | grep snd". Nothing was found. It then says to type "sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic". It cannot find linux-ubuntu-modules to install. This isn't listed in the Synaptic Package Manager either.
What do I do next?

---

### Post by markbuntu on 2009-02-04
For in depth sound troubleshooting and set up:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by GARoss on 2009-02-04
> **markbuntu said:**
> For in depth sound troubleshooting and set up:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Having lots of trouble, here.
I found your guide & was reading it about the time you posted your above message. I'm learning lots but making slow progress (8 hours so far). I installed all in this section, [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506) & none helped. I even rebooted-still nothing.

As suggested I went here next, [http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921). All seems OK except for cat /proc/asound/modules.

george@george-desktop:~$ cat /proc/asound/modules

 0 snd_emu10k1


So, it won't work without modules, right? That's what my post asked; how do I get them? I installed everything you suggested in the Synaptic Package Manager. 
Any ideas?

---

### Post by GARoss on 2009-02-04
All is well!
Near the bottom of Mark's Sound Troubleshooting Help it mentions issues with Audigy 2 SB needing the Digital/Analog toggled to **Off**. It was **On**. Switching to **Off** fixed the problem.
Thanks!:D

---

