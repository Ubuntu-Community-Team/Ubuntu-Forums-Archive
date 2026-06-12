---
title: "Help finding a thread E-MU 0404"
date: 2008-05-30
forum: Hardware
---

### Post by Sidk on 2008-05-30
Someone posted a thread with step by step instructions on getting a 0404 pci card running. I have searched till I'm blue in the face but I cannot find it.

Any chance someone knows where to find it?

---

### Post by mrtomservo on 2008-05-30
Did you mean this thread?

[http://ubuntuforums.org/showthread.php?t=441946&highlight=emu+404]("http://ubuntuforums.org/showthread.php?t=441946&highlight=emu+404")

---

### Post by Sidk on 2008-05-30
Nope, that wasn't it, but thanks for the search anyways.

It was the only instructions that worked with out a hitch. Damn, I wish I printed that page.

---

### Post by Sidk on 2008-05-30
Got it fixed, I have sound now.

Some important details left out of the wiki, You need python-dev, you need kernel headers, you need libncurses-dev. The firmware needs to be in folder /lib/firmware/emu

Install as instructed but do this to before the modprobe

$ wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
$ tar -jxvf alsa-firmware-1.0.16.tar.bz2
$ cd alsa-firmware-1.0.16
$ ./configure
$ sudo make install

---

### Post by Sidk on 2008-05-30
Got it fixed, I have sound now.

No time to fix the instructions. Try to get back to it shortly

---

### Post by lil0tik on 2008-06-02
> **Sidk said:**
> Got it fixed, I have sound now.

Some important details left out of the wiki, You need python-dev, you need kernel headers, you need libncurses-dev. The firmware needs to be in folder /lib/firmware/emu

Install as instructed but do this to before the modprobe

$ wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
$ tar -jxvf alsa-firmware-1.0.16.tar.bz2
$ cd alsa-firmware-1.0.16
$ ./configure
$ sudo make install

Hey Sidk,

Could you direct me to the (in)complete instructions you're working from.  I'm about to do a fresh install of Ubuntu 8.04 on a system with a 0404 and think I'll need all the help I can get.  It'll be a dual-boot system with XP for most of the sound utils so, in Linux, it won't need to do anything but basic playback... 

Thanks!

---

