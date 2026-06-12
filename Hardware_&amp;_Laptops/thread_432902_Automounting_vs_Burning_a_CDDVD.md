---
title: "Automounting vs Burning a CD/DVD"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by trak87 on 2007-05-04
I'm experiencing a lot of bad disk burns in Feisty. I believe there is a conflict between burning a CD/DVD and the automount program. It seems that just as I'm finishing burning a CD or DVD (in K3B) the automount program kicks in. This happens just after the data is written but before the disk is finalized, rendering the disk useless/unreadable/unmountable. Perhaps automount is being too aggressive and needs to wait until the burning has completely stopped.  I've had to resort to turning off automounting in Preferences, Removable Drives and Media, Storage.

Can anybody confirm this or maybe I'm misinterpreting what I'm experiencing. 

At the least, K3B needs to be aggressively updated in the repositories. It does seem buggy and there is an update availiable at [http://www.k3b.org/](http://www.k3b.org/)

---

### Post by trak87 on 2007-05-12
I think this was a problem with k3b more than anything because I've been able to burn from the command line without incident or automounting kicking in before it should.

---

### Post by strabes on 2007-05-12
What command did you use to burn the .iso to the disk? I'd be interested in learning how to do this without the trouble of a GUI.

---

### Post by trak87 on 2007-05-12
Command line burning is a great way to go. The only thing I haven't figured out how to do is graft disparate directories and send that to a CD/DVD. Here are some crib notes. I've got more. Note you may need to prepend sudo and adjust device names, etc.

Burning a bin/cue file with cdrdao:
```
cdrdao write -v 2 --overburn --speed 16 --device /dev/hdc --eject somefile.cue
```

Burning an iso file:
```
cdrecord driveropts=burnproof -v -sao speed=16 -dev=/dev/hdc cd.iso
```

Burn an audio cd:
```
cdrecord driveropts=burnproof -sao -v -pad speed=16 -dev=/dev/hdc -audio *.wav
```

Erase a RW disk:
```
cdrecord dev=/dev/hdc blank=fast
```

Burning a data DVD-R
```
growisofs -Z /dev/dvd -J -r -V myVolumeName somedir/
```

Burning a DVD movie from a directory that contains AUDIO_TS and VIDEO_TS directories:
```
growisofs -Z /dev/dvd -dvd-video -overburn -r -V MOVIE_NAME somedir/
```

Burning a DVD iso:
```
growisofs -Z /dev/dvd=dvd.iso
```

---

