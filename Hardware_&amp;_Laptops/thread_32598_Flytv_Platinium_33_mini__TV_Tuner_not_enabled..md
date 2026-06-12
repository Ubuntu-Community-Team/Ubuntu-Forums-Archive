---
title: "Flytv Platinium 33 mini : TV Tuner not enabled."
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by sksbir on 2005-05-08
The Flytv platinium 33 mini is a part of my notebook Gericom Cinema XXL.
This TVcard works well under windows XP with the driver and TVR software from Lifeview (see [here](http://www.lifeview.com.tw/html/downloads/internal_tv/flytv_platinum.htm) )

I found [this ](http://www.lifeview.com.tw/html/products/internal_tv/flytv_platinum_mini.htm) about my TV Tuner card : 

> FlyTV Platinum Mini  	LR212  	SAA7135  	 BTSC, EIAJ, NICAM, A2

When starting my computer, I have this in dmesg:
```

saa7133[0]: found at 0000:00:08.0, rev: 240, irq: 17, latency: 64, mmio: 0xdfffb800
saa7133[0]: subsystem: 5168:0212, board: UNKNOWN/GENERIC [card=0,autodetected]
saa7133[0]: board init: gpio is 10400
saa7133[0]: dsp access wait timeout [bit=WRR]
saa7133[0]: dsp access wait timeout [bit=WRR]
usb 2-1: device not accepting address 2, error -110
saa7133[0]: i2c eeprom 00: 68 51 12 02 10 28 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
```

my TVcard is recognized has generic, so i tried to do what is explained here:
[http://gentoo-wiki.com/index.php?title=HARDWARE_saa7134](http://gentoo-wiki.com/index.php?title=HARDWARE_saa7134)
that is, trying to detect card and tuner.

has suggested, "One way to find out your tuner number if you don't see it in the list is simple trial and error."

I wrote a shell script to do that for me:
```

#!/bin/sh
I=45
while [ $I -ge 0 ]
do
        rmmod saa7134
        rmmod tuner
        lsmod|grep saa
        lsmod|grep tuner
        sleep 2
        echo modprobe saa7134 card=$1 tuner=$I
        modprobe saa7134 card=$1 tuner=$I
        tvtime &
        PROCNUM=$!
        sleep 3
        kill $PROCNUM
        I=`expr $I - 1`
        sleep 1
done

```
so i just had to watch what tvtime give on screen. TVtime was pre-programmed on channel 22. This channel works well in my country.

I have tried all the tuner, with card 2 an 3
2 -> LifeView FlyVIDEO3000                    [5168:0138,4e42:0138]
3 -> LifeView FlyVIDEO2000                    [5168:0138]

but i don't get any image : the Tvtime interface give the choice of programming my channels, but all that i have is a black screen, with some colored "snow" witch appears briefly...
I thinks its because the tuner is not activated...

I found here more information about my device:
[http://lists.zerezo.com/video4linux/0132.html](http://lists.zerezo.com/video4linux/0132.html)

But this is a little bit to much technical...

Someone know what i can do now to get this working ?

---

### Post by stepper on 2005-05-08
Try this thread! [http://ubuntuforums.org/showthread.php?t=32371](http://ubuntuforums.org/showthread.php?t=32371)
And change the words _bttv_ into _saa7133_ also change the card number into 2 or 3.

---

### Post by sksbir on 2005-05-09
[QUOTE=stepper]Try this thread! [http://ubuntuforums.org/showthread.php?t=32371](http://ubuntuforums.org/showthread.php?t=32371)
And change the words _bttv_ into _saa7133_ also change the card number into 2 or 3.[/QUOTE]

1/ I don't have to modload anything : saa7133 is already loaded at boot.

2/ I will **not** do what you suggest until you explain me more about the saa7133 file I'm supposed to create : The options related to BTTV file are hardware dependent. options needed for saa7133 module are sure not the same.

I've tryed just one thing to show you what happens when trying to do such thing:
```

# modprobe saa7134 card=2 tuner=1 pll=1
FATAL: Error inserting saa7134 (/lib/modules/2.6.10-5-686/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 # dmesg |tail -1
saa7134: Unknown parameter `pll'

```

in the "alias" section of your example, there is "alias char-major-81 videodev"
I 'm sure i don't need this alias, because after loading saa7134, a /dev/video0 is created, witch is used by tvtime:
```
# ls -l /dev/video0
crw-rw----  1 root video **81**, 0 2005-05-09 20:43 /dev/video0
#
```

ok, so Your videodev is the same as /dev/video0.

In fact, i think that your example is outdated, or not convenient for ubuntu.


So thank's for your answer, but I'm still hoping for help...

[edit]
By scanning the content of saa7134.ko 
(string /lib/modules/2.6.10-5-686/kernel/drivers/media/video/saa7134/saa7134.ko |more )
I've got the list of videocard : 39 is 
saa7133[0]: subsystem: 5168:0212, board: LifeView FlyTV Platinum [card=39,insmod option]
(from dmesg)
This is much better (because closer to my hardware), but still don't works with all tuner ( try from 0 to 54).
This is also an another point that shows that the link [http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm) is outdated (description only until card number 33)

---

### Post by sksbir on 2005-05-13
up!
Still need help:  I know that my problem is really hardware dependant, and that my hardware is not very common, but it would be nice to get it working...

---

