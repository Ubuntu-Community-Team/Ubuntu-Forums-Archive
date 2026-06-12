---
title: "ATI Catalyst 9.2 is out!"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by zika on 2009-02-20
go and grab a new ATI catalyst 9.2 driver ... ;)
Catalyst 2.5
driver 8.582
looks promising
[http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)

---

### Post by Pitboss on 2009-02-21
I found and installed the driver, because I realized that the 9.1 driver was causing huge memory leaks. I think that 9.2 leaks too. Do you experience that or am I the only one? 

For example if I'm playing avi with mplayer in full screen, my memory usage keeps increasing, and if I run a terminal and type fglrxinfo twice the memory usage drops significantly.

EDIT: I paste the results from free, taken in 30 seconds while watching avi with smplayer in full screen mode with ao=x11. The results speak for themselves. 

```

             total       used       free     shared    buffers     cached
Mem:       2072260    1109720     962540          0      40492     458008
-/+ buffers/cache:     611220    1461040
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1327056     745204          0      40520     467624
-/+ buffers/cache:     818912    1253348
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1455112     617148          0      40536     472672
-/+ buffers/cache:     941904    1130356
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1548640     523620          0      40556     475844
-/+ buffers/cache:    1032240    1040020
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1637764     434496          0      40572     482472
-/+ buffers/cache:    1114720     957540
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1715796     356464          0      40600     486752
-/+ buffers/cache:    1188444     883816
Swap:      3903752          0    3903752
             total       used       free     shared    buffers     cached
Mem:       2072260    1785100     287160          0      40620     490180
-/+ buffers/cache:    1254300     817960
Swap:      3903752          0    3903752

```

---

### Post by Bablefish on 2009-02-21
I was want to install an ATI driver that doesn't cause me more problems than it worth.

---

### Post by binbash on 2009-02-21
Damn X11 sh.it gone at videos ?  : ) Please paste a changelog

---

### Post by radox1912 on 2009-02-21
the only thing , that 9.2 brought me, is that my cpu is working constantly at high rates..i have to use powersave options to decrease the cpu load

but still, i cannot enable compiz + opengl video playback without flickering (X11 output works fine,but has some tearing)

---

### Post by zika on 2009-02-21
can it be that these two threads have the same culprit? [http://ubuntuforums.org/showthread.php?t=1068610](http://ubuntuforums.org/showthread.php?t=1068610)

---

### Post by Pitboss on 2009-02-21
> **zika said:**
> can it be that these two threads have the same culprit? [http://ubuntuforums.org/showthread.php?t=1068610](http://ubuntuforums.org/showthread.php?t=1068610)

I don't think so. Memory usage by xorg is normal 10 ~ 13%, and it doesn't explain why typing

```

fglrxinfo;fglrxinfo

```

decreases memory usage...

---

### Post by radox1912 on 2009-02-21
and now my opengl apps stopped working ! i cannot play frets on fire, nor maniadrive.... rolling back to 9.1 and will wait for 9.3

---

### Post by zika on 2009-02-22
> **radox1912 said:**
> and now my opengl apps stopped working ! i cannot play frets on fire, nor maniadrive.... rolling back to 9.1 and will wait for 9.3
```
sudo aticonfig --overlay-type=opengl
```

---

### Post by FormerSlacker on 2009-02-22
I can add that with 9.2, using an app that uses xvideo (tvtime) and running it fullscreen causes the same behaviour.

Memory usage starts going through the roof and eventually the creen will go black and a reboot is required.

Funny bug, if you exit fullscreen and go back to windowed mode, the memory is released. Back to fullscreen, memory climbs.

Bug disappears if you disable composite.

I finally switched from Nvidia to Ati, boy what a bad move that was.

---

### Post by emshains on 2009-02-22
That's another nail in the coffin for ATI+linux.

I've never seen such bugs with nVidia.

---

### Post by Pitboss on 2009-02-22
> **FormerSlacker said:**
> I can add that with 9.2, using an app that uses xvideo (tvtime) and running it fullscreen causes the same behaviour.

Memory usage starts going through the roof and eventually the creen will go black and a reboot is required.

Funny bug, if you exit fullscreen and go back to windowed mode, the memory is released. Back to fullscreen, memory climbs.

Bug disappears if you disable composite.

I finally switched from Nvidia to Ati, boy what a bad move that was.

Tell me about it, man. :)

With me the funny bug, happens not only when playing in fullscreen but sometimes even if I start firefox. Interesting fact is that typing fglrxinfo (twice ?!) decreases memory usage...

---

### Post by zika on 2009-02-22
I've tried today to replicate Your problems and did not have any success.
please, just for fun of a test, compare Your options in "Device" section of a file /etc/X11/xorg.conf and in the "[AMDPCSROOT/SYSTEM/DDX]"section of a file /etc/ati/amdpcsdb. if they are not the same, disregarding a few from amdpcsdb that are not from xorg.conf, than we are cooking ... ;)
or, simply, post these sections of these two files.
[http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)

---

### Post by FormerSlacker on 2009-02-22
> **Pitboss said:**
> Tell me about it, man. :)

With me the funny bug, happens not only when playing in fullscreen but sometimes even if I start firefox. Interesting fact is that typing fglrxinfo (twice ?!) decreases memory usage...

That is truly bizarre!

---

### Post by FormerSlacker on 2009-02-22
Nothing fancy here.

amdpcsdb
```
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
EnableRandR12=SFALSE
RequestMSI=SFALSE
MultiviewXineramaNo3D=V1

```

xorg.conf
```
Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection
```

---

### Post by zika on 2009-02-22
> **FormerSlacker said:**
> Nothing fancy here.

amdpcsdb
```
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
EnableRandR12=SFALSE
RequestMSI=SFALSE
MultiviewXineramaNo3D=V1

```xorg.conf
```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```

answer in [http://ubuntuforums.org/showthread.php?t=1074593](http://ubuntuforums.org/showthread.php?t=1074593)

**update:**just for sake of (whim)-testing I reverted my machine to open-source video driver (ATI-radeon) from ATI restricted 9.2 and I've seen massive decrease in memory usage by Xorg. and, what is even more important, memory usage is contained regardless of kind of applications and videos etc used ... since I do not use compiz and similar stuff I'm hooked on open-source driver for some time.

---

### Post by baryah on 2009-03-02
I installed the catalyst 9.2 on my Dell D531. the video runs fine now .. BUT .. the desktop is all skewed. the right most part ( something like 2 inches of it) of the desktop is on the left, and the remaining comes after it and mouse and desktop are 'asynchronised'. I click somewhere and the effect occurs somewhere else .. argh...
Harkant

---

### Post by Pitboss on 2009-03-02
> **zika said:**
> **update:**just for sake of (whim)-testing I reverted my machine to open-source video driver (ATI-radeon) from ATI restricted 9.2 and I've seen massive decrease in memory usage by Xorg. and, what is even more important, memory usage is contained regardless of kind of applications and videos etc used ... since I do not use compiz and similar stuff I'm hooked on open-source driver for some time.

Well, goodbye compiz :( , I'm using the same driver now.

---

