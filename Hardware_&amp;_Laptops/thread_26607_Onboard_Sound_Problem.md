---
title: "Onboard Sound Problem"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by AGD on 2005-04-13
Hi guys my onboard sound doesnt seem to be detected by Ubuntu at all, infact it doesnt even detect i have sound hardware

Im using a compaq Deskpro p2

Under my BIOS setup under the onboard devices the audio is listed like so


Audio -   220-22F, 388-38B, 330-331, IRQ5, DMA1, DMA0

Does anyone have any suggestions what so ever as its realy killing me not being able to enjoy music while i work, and i fear i may have to go back to a version of windows even alough im realy loving ubuntu , sounds realy the only problem ive had

---

### Post by AGD on 2005-04-13
Ok it may be a ESS ES1868 and apprently its soundblaster compatible, i found a posting else where that says to configure the kernel like so 


--------
    * Sound card support: modular
    * Sound Blaster support
    * /dev/dsp and /dev/audio support
    * I/O base = 220
    * Sound Blaster IRQ = 5
    * Sound Blaster DMA = 1
    * Sound Blaster 16 bit DMA = 5
    * MPU 401 I/O base = 0
    * SB MPU401 IRQ = -1
    * Audio DMA buffer size = 65536
--------

But how would i go about doing that?

---

### Post by ploum on 2005-04-13
You are not alone !!!

I've exactly the same thing. I don't understand since the sound was perfect under Warty. Do you have upgraded or is this a new installation ?

The bug : [https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

Others threads :

[http://ubuntuforums.org/showthread.php?t=24916&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=24916&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=4253&page=2&pp=10&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=4253&page=2&pp=10&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3647&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3647&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3592&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3592&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3531&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3531&highlight=snd_es18xx)

---

### Post by lilandra on 2005-05-26
[QUOTE=ploum]You are not alone !!!

I've exactly the same thing. I don't understand since the sound was perfect under Warty. Do you have upgraded or is this a new installation ?

The bug : [https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

Others threads :

[http://ubuntuforums.org/showthread.php?t=24916&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=24916&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=4253&page=2&pp=10&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=4253&page=2&pp=10&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3647&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3647&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3592&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3592&highlight=snd_es18xx)
[http://ubuntuforums.org/showthread.php?t=3531&highlight=snd_es18xx](http://ubuntuforums.org/showthread.php?t=3531&highlight=snd_es18xx)[/QUOTE]
 hi
do you have to modprobe and restart also every time you reboot?
or did i break something when i installed kubuntu and started using kde?

---

