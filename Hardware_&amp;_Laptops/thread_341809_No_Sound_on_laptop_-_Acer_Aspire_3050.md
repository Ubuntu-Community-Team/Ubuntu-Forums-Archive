---
title: "No Sound on laptop - Acer Aspire 3050"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by FooAtari on 2007-01-19
Ok, I think this is the fourth time I have tried to move to Linux in the last few years...

I love my games, and that has kept from moving completely to linux however I have installed dual boot on my PC several times, I've just never stuck it for some reason, or run of disk space so linux got the boot.

However I do not play games on the laptop, so I see no reason why I can't completely remove Windows from my laptop, as long as it all works. Well thats a lie i do have WoW installed, but im going to look at Cadega to run that.  It's not essential though.

Last time I had huge difficulties with wireless, but on this laptop it was a doddle.  However I have another problem I didn't expect, no sound....

Here is some info that might help

aplay -l
allie@Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

lspci -v
Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 233
        Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I have had a quick scan about the forums but nothing seems to be helping.  Anyone know of a solution for this? I think im good to go, as long as I can get my hardware sorted.

Thanks a lot :D

---

### Post by zshift on 2007-01-19
I have a gateway MX7527 and I have the same issue. Only randomly does my sound work, and it only works if it worked from boot time. 

peter@Gateway-MX7527:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

from the above, I noticed that my speakers were missing, which are Conexant. I'm not sure if that makes a difference, but all in all it souds like we have the same issue.

---

### Post by FooAtari on 2007-01-20
I thought I had fixed this but no.

When I first installed Ubuntu I run alsamixer, and when I turned up the surround sound option I had sound.

After restarting the laptop i had no sound again, so I tried to run alsamixer again, but I cant;

alsamixer: function snd_mixer_load failed: Invalid argument

Anyone know how to fix this?

---

### Post by maumau on 2007-01-20
Try to launch from term
```
alsamixer -V all
```

ensure that PCM does enable (press M to do) than encrease the volume

ciao

---

### Post by FooAtari on 2007-01-20
Thanks but that was a no go. same error :(

---

### Post by bigdogpc on 2007-02-02
I guess I am joining a non-exclusive club, I have the same no sound problem on the Acer Aspire 3050.  The install of Edgy was cake and as best I can tell, everything works like a champ EXCEPT the sound.  I am a noob even after trying many flavors of Linux.  Command line stuff makes me nervous since I am aware of my own ignorance.  IF somebody figures out the sound problem, PLEASE post the fix in terms I can follow.  Ya'll have a great day!  Thanks

---

### Post by oasill on 2007-02-03
I also have an Aspire 3050 and it seems that the sound is on but is available only through the earphones and not from the speakers! This somehow would imply that a switch is missing. I tried to check if the state of the MS-Win setting influences the state after boot (far fetched attempt but still). No help.

Do you get the wireless lan to work correctly?
          
                              rgds OA

---

### Post by bigdogpc on 2007-02-05
I ASSUME the wifi is working since the light is on but I have not tried it since I am plugged in to normal network.  Yes, I have sound through the headphones.  pci hda-intel is the card setup I have at the moment.  Good luck to ya!  I am still plugging away at mine.

---

### Post by ivansv on 2007-02-05
don't know why this is not common knowledge by now, laptops on linux neednto have acpi disabled at install time or the sound will not work. most laptops come with a windows acpi which corrupts acpi in linux.
on ubuntu when you install at boot time press F6 and at the bottom of the page you will see a line of boot parameters, just add acpi=off at the end and proceed with a normal install, when you reboot into ubuntu you will have sound.

---

### Post by oldone on 2007-02-05
Ivansv:



I have this machine coming soon. I am absolutley new to linux and ubuntu and even a windows machine coming from Macs.

so can you please explain the complete process more clearly and in detail.

I appreciate all your help.

---

### Post by ivansv on 2007-02-05
happy to, most laptops that people dual boot with linux come with windows preinstalled. the mfgr. and pc resellers have an acpi setup for windows but it corrupts acpi on linux with no sound as a result. i once researched the problem and its complicated to resolve-to end up with an acpi that works well with linux- it even involves recompiling the kernel, too complicated for most linux users.
the simple thing is to install linux with acpi=off and you'll have sound and apm for your battery power, recharge, etc. i've tried this with my laptop and a few linux oss, works everytime, if i installed with acpi enabled in the kernel-no sound. just follow the procedure in my last post you'll be ok.
i don't know why there isn't a wiki entry on this by now its a common problem just read some of the posts, it comes up often.

---

### Post by oldone on 2007-02-05
Ok thank you for the extra info but I am lost as to exactly when in this whole install process to do what i need to do.

Thank you for your patience....

i guess I need the paint by numbers version.

I am installing totally over the windows that comes on this new machine.  I want notta left.

all Ubuntu.

i guess i need a 512 mb bios partiton of some sort; 2 GB of swap file and the rest root or whatever it is technically called.

thanks you - any more counsel would be most, most appreciated!

---

