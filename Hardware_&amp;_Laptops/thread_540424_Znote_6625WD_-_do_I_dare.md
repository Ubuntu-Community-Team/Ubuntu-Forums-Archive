---
title: "Znote 6625WD - do I dare?"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by martinrandau on 2007-09-01
I am very interested in buying a Znote 6625WD laptop. Here are the specs:

15,4" WSXGA+ 1680x1050 - 6625WD
2048MB (2x1024) DDR2 667/PC5300 SODIMM
NVIDIA® Geforce 8600M GT
160GB SATA 2,5" 5400RPM - SAMSUNG
6 Cell batteri
Intel Pro/Wireless 4965AGN - 300Mbit
SAMSUNG DVD-RW Dual-Layer 
1.80 GHz Intel® Core™2 Duo T7100 800MHz

As far as I can see there shouldn't be any problems hardware-wise. The wlan can be tricky but I have seen lots of people getting it to work.

What do you think? Any advice is appreciated!

---

### Post by Corentin38 on 2007-09-01
I got a zepto 6224W last week with the same soundcard (ALC268), the same wifi, the same dvd drive, as I remember ...
Nothing work with feisty
All is working perfectly with Gusty, but the sound ...
The sound problem can be resolved by compiling the new ALSA drivers 1.0.14 with a patch. but I didn't succed ... :/
More info here : [http://ubuntuforums.org/showthread.php?p=3290705&posted=1#post3290705](http://ubuntuforums.org/showthread.php?p=3290705&posted=1#post3290705)

Corentin

---

### Post by nosrednaekim on 2007-09-01
you might need to use the alternate installer, but yeah, everything on there should work. With gutsy you will be able to use the liveCD installer if the fiesty one doesn't work.

---

### Post by martinrandau on 2007-09-01
Right, thanks for your reply. That's good news. I'm also thinking about this, for the same price but with a santa rosa processor:

Znote 3415W
2.20 GHz Intel® Core™2 Duo T7700 800MHz
Intel Pro/Wireless 4965AGN - 300Mbit
SAMSUNG DVD-RW Dual-Layer 
15,4" WXGA 1280x800 - 3415W
NVIDIA® Geforce 8600M GT
120GB 5400rpm SATA Harddisk
9 Cell Batteri 2x25W/3x15W
2 GB DDR2 667/PC5300 SODIMM

Processor is better but newer, which might be bad...

---

### Post by Corentin38 on 2007-09-01
You can resolve all the problems of the zepto computers by searching a little, but DON'T CHOOSE a hybrid hard drive ...!

---

### Post by martinrandau on 2007-09-01
What is a hybrid harddrive?

---

### Post by nille on 2007-09-10
> **Corentin38 said:**
> I got a zepto 6224W last week with the same soundcard (ALC268), the same wifi, the same dvd drive, as I remember ...
Nothing work with feisty
All is working perfectly with Gusty, but the sound ...
The sound problem can be resolved by compiling the new ALSA drivers 1.0.14 with a patch. but I didn't succed ... :/
More info here : [http://ubuntuforums.org/showthread.php?p=3290705&posted=1#post3290705](http://ubuntuforums.org/showthread.php?p=3290705&posted=1#post3290705)

Corentin

I have managed to get the 6224W to work quite nice with Feisty, but there's still some major bugs. (That is: do not run Fiesty, Gutsy is stable enough).

The soundcard works great with the ALSA 1.0.15rc1 which was released about two weeks ago. Just download the files (-driver, -lib and -utils), compile using the instructions here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and then add the following line at the end of the file /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=toshiba
```

---

### Post by martinrandau on 2007-09-13
Got my laptop and everything works great... except from the sound. Will try the latest alsa drivers later.

---

### Post by nidelius on 2007-11-02
I've got it 2! I have gutsy installed and I'm trying to get the sound this moment. The other problem I have encounterd though is that the CD/DVD is not detected.

---

### Post by jespdj on 2007-11-02
> **martinrandau said:**
> Right, thanks for your reply. That's good news. I'm also thinking about this, for the same price but with a santa rosa processor:

Znote 3415W
...
The Znote 6625WD is also a Santa Rosa laptop.

Santa Rosa is not the name of the processor, but of Intel's new chipset for laptops.

---

