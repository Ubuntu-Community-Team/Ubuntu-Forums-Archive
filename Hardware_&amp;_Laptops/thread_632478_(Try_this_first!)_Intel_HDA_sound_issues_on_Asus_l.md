---
title: "(Try this first!) Intel HDA sound issues on Asus laptops"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by phyzik on 2007-12-05
Ok guys, sorry for a new thread, but I felt the need to try and help my fellow Ubuntuers-on-Asus.

There are tons of active threads on ubuntuforums.org and dozens of other sites considering sound issues with Intel HDA sound cards (with Realtek chips), and there are at least a dozen of different solutions.

I just want to point everyone to try THIS solution first, (it worked for me, but only on a clean installation) because it is by fare the easiest and you can undo it in a second. So,

open the terminal and type
```
sudo gedit /etc/modprobe.d/alsa-base
```

go to the end of the file and add a new line:
```
options snd-hda-intel model=lenovo
```

and restart the computer.

That's it (don't forget to check all your sound channels are not muted). It should work for F3 and Z53 laptops, maybe even other models.

If it's working, well, congratulations :) If not, I'm really sorry, but you'll have to just delete that line and try one of the other solutions (like installing new alsa drivers from source and running alsaconf)

Good luck!

---

### Post by weirdfrog on 2007-12-10
Hi there--

On at least a couple of Asus laptop models (A8DC-A1 and F3SA-A1) and possibly others (F9DC ?)-- that options line must be added to /etc/modprobe.conf instead of /etc/modprobe.d/alsa-base.
Took me forever to figure that out--- *whew!*
(and I'm a total linux newbie, so I don't know WHY that works, but it does.)

Now if I could just figure out a way to get more volume outta those crappy lappy external speakers...

---

### Post by manugap on 2007-12-21
Hi, 
this trick (/etc/modprobe.d/alsa-base) worked perfectly on my ASUS PRO31S (F3Sa), while running ubuntu 7.1 with all the software updated.
Thanks !!

manu

---

### Post by ppi on 2007-12-21
Hi,
it works fine on Asus F3SC. My wife can listen music on new laptop :).
Thanks :)

---

### Post by weirdfrog on 2007-12-22
Hey ppi-- which worked for you? adding the options line in /etc/modprobe.d/alsa-base  or in /etc/modprobe.conf?
 I'm curious 'cause it seems to vary between Asus models...

---

### Post by ppi on 2008-01-03
Hi,
I have added:
options snd-hda-intel model=lenovo
in:
/etc/modprobe.d/alsa-base

I'm using Kubuntu 7.10 with latest updates on Asus F3SC-AP200C

---

### Post by Leighton on 2008-02-06
Hey guys,

im running an F9DC, and Ubuntu 7.10. Had no sound whatsoever,  i added

options snd-hda-intel model=lenovo
to /etc/modprobe.d/alsa-base

quick reboot and bam! Works a treat!  All standard drivers etc.

Thanks for the fix!


onto the next issue...

Leighton.

---

### Post by sgleo87 on 2008-02-06
worked for me on my asus v1s, also added: options snd-hda-intel model=lenovo to /etc/modprobe.d/alsa-base, running ubuntu 7.10

---

