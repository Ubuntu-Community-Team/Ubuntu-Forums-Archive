---
title: "Upgrade 9.04 to 9.10 - No Sound"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by moddinati on 2009-11-05
Hello,

I just updated from 9.04 to 9.10 and now my sound card is not recognized.  Here is some more info.

```

> aplay -l
aplay: device_list:223: no soundcards found...

``````

> lspci
....
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
.....

```My sound worked fine in 9.04. Your help is appreciated

---

### Post by blakeivey on 2009-11-07
I am having the same problem. I upgraded to 9.10 yesterday and just noticed that the sound was not working. 

lspci | grep audio returns : 08:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

aplay -l returns: aplay: device_list:223: no soundcards found...

Anyone know how to get the sound to work again?

---

### Post by blakeivey on 2009-11-07
I used the advice from : [http://ubuntuforums.org/showpost.php?p=8212837&postcount=4](http://ubuntuforums.org/showpost.php?p=8212837&postcount=4) and it corrected my USB problem and the sound problem. I just edited my first entry in the menu.lst with the new kernel version. 

Thats it :-)

Blake

---

### Post by ricardo.gloe on 2009-11-07
I uninstalled PulseAudio and installed esound from the synaptic package manager and got the sound back. 

Lost the volume icon from the tray though. 
Still working on that.

---

### Post by moddinati on 2009-11-10
thanks blakeivy, fixing my menu.lst fixed the problem.

---

