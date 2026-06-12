---
title: "so my sound just died"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by band-aid on 2007-01-05
Well my other thread didn't post so here we go again.

My sound was working fine last night. Today I went to watch a youtube video and realized that I had no sound. All the little bars in the mixer are maxed out and nothing is muted. The only thing I have installed recently was beryl and sound was working fine with it last night. I am quite confused as to why it just stopped working.

Also, what are these codecs that Automatix tells me are illegal?

Band-aid

---

### Post by jms1989 on 2007-01-05
I'm in the same boat as you are. My sound just died about 10 minutes ago and now amarok won't play any sound. It stoped after I pressed pause.

Please help us!!

---

### Post by band-aid on 2007-01-05
if yours has done the same thing it may have to do with a recent update... or we both screwed up the same thing at the same time.

---

### Post by band-aid on 2007-01-06
anyone?

This is pretty major. Now I have to boot into windows to do anything that needs sound.

---

### Post by wildkarde on 2007-01-06
hey, so my sound just died as well.   damn beryl....

help us anyone?

---

### Post by janmartin on 2007-01-06
Hi all,

assuming you are running Ubuntu 6.10 Edgy Eft it might be an idea to update to the newest stable ALSA driver.

At my laptop sometimes the sound won't work when a external USB hard drive is plugged in. 
Also it lost the sound level setting during reboot.

You could try to update ALSA from 1.0.12rc1 to 1.0.13 .

_Try to find out a bit before you start._
**aplay -l**
Will list the Sound hardware:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
And 
**cat /proc/asound/version**
will list your existing driver version:
```
Advanced Linux Sound Architecture Driver Version **1.0.12rc1** (Thu Jun 22 13:55:50 2006 UTC).
```

Check out [http://www.alsa-project.org](http://www.alsa-project.org) if your hardware is mentioned in the changelog.

Preparations:
Follow this guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29)

Download from
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2)
Unpack it. 
In the directory do:

```
./configure
make
sudo make install
```

Reboot.

Check driver version again:
```
jan@jan-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version **1.0.13**.
Compiled on Jan  4 2007 for kernel 2.6.17-10-generic (SMP).
```

So far my sound works perfect now when USB HDD is plugged in. Sound levels are remembered after reboot.

Good luck and post your hardware and if it works for you.

---

### Post by Maxcribbin on 2007-01-06
Had the same problem today. worked fine all morning but now stopped working.
Must be a bad update?

Carl.

---

### Post by jms1989 on 2007-01-06
Hmm that's good but I'm using Dapper.

My sound will sometimes work. Currently, it will play a song then it will show about 12 errors then the app will stop working. I guess it has something to do with the sound driver.

I have two sound cards; one is a PCI card and the other is hard wired to the motherboard.

---

### Post by wildkarde on 2007-01-06
I don't think it's a bad update.  Trying to install the new ALSA drivers for 1.0.13 as the previous poster said, i came across this message.  

```
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

```

The installation failed shortly after complaining that i was attempting to edit modules on the kernel.  Should've saved the log.  <shrugs>

Anyway, I installed gnome-alsamixer as it (the sound) stopped working after an update which led me to believe that there was a sound update... and the mixer channels were muted.

Un-muted then and my sound is back.  Woo!

Hope this helps.

EDIT::  

janmartin's howto specified to use 'make install' but i opted to go with checkinstall which is probably the reason why my install failed.  I don't think we need to install anything else as channels are just muted.  (Just in case i didn't make it clear enough :p)

---

### Post by jms1989 on 2007-01-06
I'm getting this error...

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

What do I need to install?

---

### Post by 8086ed on 2007-01-07
I installed beryl on edgy and my sound started working, but after installing gnome-alsamixer like wildkarde suggested, then unmuting all of the channels, it works!  Thanks for the tip, wildkarde!

---

### Post by janmartin on 2007-01-07
@ jms1989,

I have not tried this with Dapper.
Are you sure you haven't skipped the Preparations:
[http://ubuntuguide.org/wiki/Ubuntu_E...d-essential.29](http://ubuntuguide.org/wiki/Ubuntu_E...d-essential.29)

@ wildkarde

I got the Warning too and I didn't install anything additional. I just worked. So you might be fine if you try again with 'make install'.

Anyway, have you checked **cat /proc/asound/version** to find out if a new driver has been installed at all?

Jan

---

### Post by band-aid on 2007-01-07
ok well I am trying to install the drivers, and I already had to point the configure script to the correct are for the headers (version.h) but now it gives me this 

configure: error: you have ALSA built into your kernel.

and this is beyond my knowledge.  Why would that make any difference in updating it? Why can't they just release a precompiled binary :D

---

### Post by wildkarde on 2007-01-07
@janmartin: i don't doubt it will work with make install but this sold me:

> Use CheckInstall instead of just running "sudo make install", as that will likely put files all over the filesystem, with no easy way of removing them if things go wrong. If in the future you try to install a package that contains the same file as the software you are compiling, you will receive errors and the software you compiled may stop working.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Plus sound is working.  :)

---

### Post by Killerah on 2007-01-07
I'm starting to suspect Beryl is the problem behind this. I too have Ubuntu Edgy installed, and all of a sudden after a reboot after installing some stuff, I have no sound and no idea why it stopped or how to get it back. In fact, I don't think my computer knows there's anything wrong with it because in the past when I've had sound card issues my card wouldn't show up in the mixer and/or Amarok wouldn't play anything at all, but Amarok plays (just no sound comes out), and my card shows up in the alsa mixer (and everything's unmuted), but still no luck! If a solution is devised I would like to know what it is so I can start using Ubuntu again, until then I have to stick with windows (I need my music).

---

### Post by jms1989 on 2007-01-07
> **janmartin said:**
> @ jms1989,

I have not tried this with Dapper.
Are you sure you haven't skipped the Preparations:
[http://ubuntuguide.org/wiki/Ubuntu_E...d-essential.29](http://ubuntuguide.org/wiki/Ubuntu_E...d-essential.29)

@ wildkarde

I got the Warning too and I didn't install anything additional. I just worked. So you might be fine if you try again with 'make install'.

Anyway, have you checked **cat /proc/asound/version** to find out if a new driver has been installed at all?

Jan

No I didn't skip the preparations, they were already installed. This is not something I can go a long time without and I'm not ready for the upgrade to edgy. If it helps, I'm using a desktop pc.

---

### Post by JulesBl on 2007-01-08
Me too, running dapper, no changes to anything except installing the alternative flash plugin and doing an update.

Symptoms:
Sound plays during startup and logoff, other than that not a peep, the alsa sound system is not muted and can still see my imic no problem, there dont seem to be any errors associated with the sound system.

Jules

---

### Post by jms1989 on 2007-01-09
Please, someone help us... we really need our sound fixed.

Update: I decided to remove my second sound card because it was conflicting with my operations.

---

### Post by Killerah on 2007-01-10
Mine's still screwed up. Actually I should mention that before it died completely the sound that comes integrated into my mobo was working out of the right channel. But now not even that works. As jms said, somebody please help I really need to get this worked out.

---

### Post by popkid on 2007-01-10
My Sound Died too a couple of days back, I'm using dapper btw, must have been about same time as yours, but my laptop is pretty ancient and I figured the card had just died. (A maestro 2E) ... until I happened to be using the dapper install disc to show a friend the live desktop... and my sound worked... Puzzled, I searched and found this thread and installing gnome alsa-mixer and unmuting then fiddling with the levels works a treat, thanks guys....

It would seem something strange happened with one of the updates though, not sounding like coincidence....

pK;)

---

### Post by Killerah on 2007-01-12
Ok, I got mine working, all I did was uninstall the third party flash plugin that came with automatix and then do a reboot. Afterwards I installed it using synaptic and rebooted, now it works just fine. Hope that works for you too jms, if not I'm sorry that I have to leave you all alone in the "sound not working" party.

---

### Post by sipstar on 2007-01-13
Same sound issue here with the internal soundcard on my shuttle (SN41v2).
Tried all kinds of things and every setting seemed ok but no sound came out of any speakers/headphones i tested. Installed a PCI-soundcard and sound was working out of that card.
[COLOR="SeaGreen"]After installing the gnome-alsamixer and unmuting a few channels the internal card is up and working again.[/COLOR]
I called up a friend who was experiencing the same problem on his laptops built-in soundcard and the gnome-alsamixer solved his problems as well.

Are you guys experiencing these issues with internal soundcards?

guess its an update issue anyways..

cheers!

---

### Post by Killerah on 2007-01-16
Hmm, back to the same old problem again, I guess it wasn't the flash thing, it's just that my sound card is flaking out. Only in Ubuntu though, and just about every other reboot.

---

