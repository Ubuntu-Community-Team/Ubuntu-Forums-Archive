---
title: "Synaptic (but not D/L speed) sluggish"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by Rinias on 2009-02-17
Hello,

I have 8.10 x86-64 on two different laptops (different processors, RAM, etc). When I install, Synaptic runs with no problems. After a while, however, both systems display the same problem :

The dependency checking (after one selects "install") as well as the clean-up, but not the downloading nor the installing, is very slow. Synaptic freezes and runs - bizarrely ? Does it only run on a single processor? - the first processor at 100% while the second hangs around 8% (on both systems).

Besides the obvious processor use, this does not affect the desktop nor the other applications. After 25 seconds to one minute, Synaptic comes back with no apparent problems. The downloading and installing go smoothly, but Synaptic hangs again when it is returning to the "main" screen.

I believe that this problem has to do with Synaptic only - apt-get works as rapidly as usual.

I found this post : [http://ubuntuforums.org/showthread.php?t=831761&highlight=synaptic+slow](http://ubuntuforums.org/showthread.php?t=831761&highlight=synaptic+slow) but upon inspection of the files in /usr/lib/mime/packages found no "bin" files. There are, however, sun-java6-bin and texlive-base-bin. These are readable text files, however. Furthermore, it is not "update-mime" that takes the processor but rather "synaptic" itself. 

Is there any reason that Synaptic suddenly starts to hang? There seems to be no particular update that makes this happen - both systems were updated simultaneously and one computer started having this problem a week before the other. Perhaps there is some sort of clean-up that I have overlooked for apt?

Thanks in advance,

Rinias

---

### Post by yoyoned on 2009-02-17
syanptic is just slow at times.  Very few applications can sue multiple CPUs.  An app has to be coded to use parallel processes.

---

