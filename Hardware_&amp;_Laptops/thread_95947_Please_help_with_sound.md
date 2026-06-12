---
title: "Please help with sound"
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by doublesix on 2005-11-27
Hello everyone. I am new to Ubuntu but not so much to linux. I have installed Breezy on a Toshiba 2530CDS laptop, and everything is great, but there is no sound.

I previously installed Kubuntu Breezy on this machine, but decided to try Ubuntu as Gnome seems to be more responsive on this model, since I only have 96MB RAM. In kubuntu, getting sound was as as simple as doing a sudo modprobe opl3sa2 and then adding opl3sa2 to the /etc/modules file.

Unfortunately, the same does not apparently work for Ubuntu. Can anyone tell me step by step how to enable sound? Everything else is working great.

My info is as follows, from the BIOS:

WSS I/O Address - 530H
SBPro I/O Address - 220H
Synth I/O Address - 388H
WSS & SBPro & MPU IRQ - 5
WSS DMA - 1
SBPro DMA - 0
Control I/O Address - 370H
MPU401 Interface - 330H

Thanks in advance for your help.

---

### Post by Zimmer on 2005-11-27
The wiki sorts most of my problems...drivers, games etc.
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)
might help.
But sound seems to be the Black Art for Ubuntu..
There are many threads out there and most of them confused the heck out of me probably due to the variety of cards and systems and legacy stuff(Linux  sound software).
I had sound working 'out of the box' as it were, XMMS played stuff, hovering over music files produced the sounds (that was wierd the first time I noticed that, mainly because I have  wireless headphone setup and I tend only to wear that for games..) so I got sound working in Wolf ET using the wiki hints and previous experience of Fedora and thought no more of it. Until..I wanted to edit a sound file recording captured using a Windwoes XP laptop, using Audacity. I had used Audacity on Hoary so I was surprised when I started it and got an error and no sound..
So I have altered the (Un) Enlightened Sound Daemon config file in a manner that helps Wolf ET and then disabled the sounds for events in  the System Preferences Sound menu.
No nice tunes at startup, and probably no disturbing beeps and clonks when things don't go right (but that's how it was in the Office, no soundcards on desktops ). But, Audacity works XMMS plays music and Totem is playing DVDs OK...for me , It may not be working perfecly, but I don't KNOW that so Job Done.(for now)
I must mention that I used Easy Ubuntu to set up some of my stuff (and that enabled DMA support for the CD drive, which  helps..
[http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23](http://placelibre.ath.cx/keyes/index.php/2005/09/29/45-easy-ubuntu-23)
version 2.4 now..
You might have a simple problem like the sound is muted, in which case check the ALSA mixer settings (there are many threads going into great detail about that, so I won't repeat)
this is my /etc/esound/esd.conf    contents in case you would like to try that first.
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5

Best Regards

Zimmer

---

### Post by doublesix on 2005-11-28
Thanks for the info, but I'm still not having much luck. I can get the Multimedia System Selector to play a test sound, but only after doing a sudo modprobe opl3sa2 and setting the output to OSS. Alsa will not work. I don't even seem to have an alsaconfig command. However if I put opl3sa2 in the modules file, the sound won't work. I have to go through the terminal at each boot to get just that test sound, but no other sounds work.

---

### Post by Zimmer on 2005-11-29
Hello
Check which souncard you actually have....
Have a look here:
[http://ubuntuforums.org/showthread.php?t=67398&highlight=opl3sa2](http://ubuntuforums.org/showthread.php?t=67398&highlight=opl3sa2)

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)
quote:
Note that there was a rewrite of a lot of the sound core and related drivers. The older stuff is generally called OSS' and the newer is called ALSA'. The intention is to drop the OSS stuff eventually. To avoid name conflict, the ALSA stuff generally has `snd-' as a prefix to all the boot parameters.
so the module parameter is perhaps:
snd-opl3sa2= Yamaha OPL3SA2

Does this help??

Zimmer

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

