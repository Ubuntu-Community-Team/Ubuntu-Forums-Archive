---
title: "Xorg problems after upgrading from 8.10 to 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by funkiwan on 2009-04-27
I upgraded to 9.04 and am noticing several problems with my system. 

1. Occasionally, the screen doesn't draw itself properly. See example here:

[http://img216.imageshack.us/img216/4269/wonkyscreen.png](http://img216.imageshack.us/img216/4269/wonkyscreen.png)

2. X seems to be working pretty hard with relatively little work. It seems to idle at 20% cpu and often times spikes over 50% for no obvious reason.

I don't have desktop effects enabled. 

Here's my info:

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

$ grep /drivers /var/log/Xorg.0.log
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so

$ uname -a
Linux kubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by funkiwan on 2009-05-07
After a bit of searching the web, it seemed I didn't really have any other driver options so I decided to try and muck with my xorg.conf file. The following has fixed both my performance and display problems:

```

Section "Device"
        Identifier      "Configured Video Device"
        Option "MigrationHeuristic" "greedy"
        Option "AccelMethod" "XAA"
        Option "AccelDFS" "true"
        Option "AGPMode" "4"
        #Option "EnablePageFlip" "true"
        #Option "EnableDepthMoves" "true"
EndSection
```

Links which I found helpful were [here]("http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html") and [here]("http://ubuntuforums.org/archive/index.php/t-396671.html"). I've commented out the last two options because I experienced other weird display options (didn't seem to be repainting properly). It's possible (probable) that there's a better set of options for my system. If anyone knows of any tools/resources out there, please send them along.

Hope this helps someone.

---

### Post by chemamar on 2009-05-07
Man, thank you very much!!!!!!!!!!:)
All my problems with my graphics have been solved just adding those miraculous lines!

I had thought that my card was severely damaged because I could not see properly anything, but now my graphics look better even than when using windows xp and the ati propietary drivers.

If anyone else wants to try, in my case:```
jose@jose-desktop:/etc/X11$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]

```
```
jose@jose-desktop:/etc/X11$ grep /drivers /var/log/Xorg.0.log
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so

```
```
jose@jose-desktop:/etc/X11$ uname -a
Linux jose-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```

---

### Post by chemamar on 2009-05-23
I would like to share with anybody using ati radeon 9800 pro the following xorg.conf that has improved even more my ati performance. I am using open source drivers.

Here is my xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option "MigrationHeuristic" "greedy"
        Option "AccelMethod" "EXA"
        Option "AccelDFS" "true"
        Option "AGPMode" "8"
	Option "FBTexPercent" "0" # see http://foros.ubuntu-cl.org/viewtopic.php?p=37255  
#The last option has improved my fps from 2800 to 3400      
EndSection

```

I hope this can help more people!

---

### Post by megazayed on 2009-05-25
hi all this is my setting can any one help me in this

> 
root@ahmed-laptop:/etc# uname -a
Linux ahmed-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


> 
root@ahmed-laptop:/home/ahmed# sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) 


thanks

---

