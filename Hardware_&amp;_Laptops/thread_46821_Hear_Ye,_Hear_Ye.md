---
title: "Hear Ye, Hear Ye?"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by tidge on 2005-07-06
Hi All

I've been working with linux since RH7.0 and have recently tried to convert to Ubuntu 5.04.

I write LAMP software for medical practice and research and run several web servers. I have degrees in science and medicine, but no formal training in IT - just started programming with an Apple ][+ back in 1982.

I have a new P4 with Intel motherboard and onboard 82801FB (ICH6) audio controller - pretty standard hardware. Kernel modules weren't installed for it automatically, so I trawled the web for support. What I found was pretty much what you're looking at on this site - loads of mute machines.

I have to keep focus on what is important to my business, and sound is not. I have tried all the quick fix options presented on this site and others and fiddled with the BIOS settings and reinstalled and reinstalled, but still have no sound.

I'd like to promote and use Ubuntu but it is impossible when standard hardware is not detected and configured automatically at installation.

If there is an Ubuntu developer out there who reads this and feels that there is a major problem with sound installation, please get a patch or an effective repair guide together quickly.

---

### Post by intangible on 2005-07-06
Hardware support is one of those things that isn't difficult to do, except when the manufacturer of said hardware refuses to release information on how to talk to the hardware, or they refuse to release a driver for your favorite operating system.  When that happens, you are stuck with having to reverse-engineer everything, and that is not an ideal situation.

Anyway, the sound drivers included with Ubuntu don't detect that chip by default, there is a work-around, follow this guide here: [https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto) ; The second method seems to be a cleaner way to do it.  I'd bet the next version of Ubuntu will have support for that chipset out of the box.

---

### Post by tidge on 2005-07-13
thank you, thank you - so easy when you know how or where!

---

### Post by blaha on 2005-07-13
> 
Anyway, the sound drivers included with Ubuntu don't detect that chip by default, there is a work-around, follow this guide here: [https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto) ; The second method seems to be a cleaner way to do it.
That doesn't work for me :(

I had to use the second alternative, with apt-get, because I couldn't compile the driver form the alsa site. 

Everything seemed to work until the last line.

When i enter: 
dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
It tells me that **"that file or directory does not exist"**, even though the previous command [B]"processed fine"
[/B]

---

### Post by ThatRickGuy on 2005-07-23
I'm getting the same error. I'm using the 686-smp kernel though, so I've been inserting -smp into all of the 686 references, but it's not working for that line.

```

root@udev:/usr/src/linux-headers-2.6.10-5-686-smp # dpkg -i alsa-modules-2.6.10-5-686-smp_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-686-smp_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686-smp_1.0.8-4ubuntu4+10.00.Custom_i386.deb
root@udev:/usr/src/linux-headers-2.6.10-5-686-smp #

```

-Rick

---

