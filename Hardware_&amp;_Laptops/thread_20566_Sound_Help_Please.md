---
title: "Sound Help Please"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by Drakx on 2005-03-17
Hey Guys :D

Well this seems to be a common thing so im gonna ask as well :D

I dont have sound at all nothing, nada

im system is as follows

AMD Athlon Xp 3200 (Barton)
2 GIG ram
nForce 2 Ultra 400 motherboard
On Board sound (mandrke 10.1 used snd_intel8x0 for my sound card since removed thats to below)
ATI X800 PRO (got working thank to [this :D](http://www.ubuntuforums.org/showthread.php?t=3567) )

Also it was a long time ago when i downloaded (but did not install till yesterday) Ubuntu so i cannot remember which version i have i can tell you im using XFree 86 4.3 (if that helps) and my kernel is 2.6.8.1-3-386

thanks guys

also one other thing how do i bring up the fps in ut2004?

---

### Post by Drakx on 2005-03-17
Any body please i tryed installing the nvidia drivers for my board but it complains that im using the wrong kernel headers my kernel is 2.6.8.1-3-386
 and my kernel headers are linux-headers-2.6.8.1-3  linux-headers-2.6.8.1-3-386 (dunno which one but thats there :D also i found out what version im using and thats 4.10 

im also getting this

```
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
``` 

also when i come to installing the nvidia sound drivers i get 

```
gcc-version-check failed:

  ./nvsound/main/conftest.sh: line 1: cc: command not found
  Could not compile gcc-version-check.c

  If you know what you are doing and want to ignore the gcc version check,
  select "No" to continue installation.  Otherwise, select "Yes" to abort
  installation, set the CC environment variable to the name of the compiler
  used to compile your kernel, and restart installation.  Abort now?
``` 

thats after following this : [http://www.nvnews.net/vbulletin/showthread.php?t=43177](http://www.nvnews.net/vbulletin/showthread.php?t=43177)

Thank you

---

### Post by Drakx on 2005-03-17
No one knows? ah please im beggin here i really need sound oh and thats the only thing thats keeping me in windows for my UT 2004 and team speak

---

### Post by njs12345 on 2005-03-20
[QUOTE=Drakx]Any body please i tryed installing the nvidia drivers for my board but it complains that im using the wrong kernel headers my kernel is 2.6.8.1-3-386
 and my kernel headers are linux-headers-2.6.8.1-3  linux-headers-2.6.8.1-3-386 (dunno which one but thats there :D also i found out what version im using and thats 4.10 

im also getting this

```
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
``` 

also when i come to installing the nvidia sound drivers i get 

```
gcc-version-check failed:

  ./nvsound/main/conftest.sh: line 1: cc: command not found
  Could not compile gcc-version-check.c

  If you know what you are doing and want to ignore the gcc version check,
  select "No" to continue installation.  Otherwise, select "Yes" to abort
  installation, set the CC environment variable to the name of the compiler
  used to compile your kernel, and restart installation.  Abort now?
``` 

thats after following this : [http://www.nvnews.net/vbulletin/showthread.php?t=43177](http://www.nvnews.net/vbulletin/showthread.php?t=43177)

Thank you[/QUOTE]
 For your nVidia driver issues, try running
```

sudo apt-get install build-essential

```
That'll install you a C compiler, which is what you need to compile the dirvers. Alternatively, you can follow the howto at [http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) .

---

