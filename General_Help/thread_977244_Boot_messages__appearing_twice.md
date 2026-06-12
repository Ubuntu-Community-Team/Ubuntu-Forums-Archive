---
title: "Boot messages  appearing twice"
date: 2008-11-10
forum: General Help
---

### Post by blazemore on 2008-11-10
When I boot my system (I don't use usplash), most (but not all) boot messages appear twice, one after the other.
For example:

[    4.384243] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[    4.384280] scsi 2:0:1:0: Attached scsi generic sg2 type 5

I think it's having an impact on my boot time.
Profiling isn't enabled.

How do I enable bootlogging so I can show you which ones duplicate?

I know, for example. that Setting System Time only appears once.
Also, each pair only gets one [ OK ], on the second one.

---

### Post by jolx on 2008-11-10
those two are actually different - the first one is sg1, the second is sg2.

which means they will be doing two different things, not the same thing twice.

how long is your boot time (not including POST)?

---

### Post by blazemore on 2008-11-10
Okay that wasn't an example of ACTUAL boot text, so ignore it.
The boot time isn't too shabby; 22 seconds from end of grub to login screen.
An example of text that duplicates is
* Reading files needed to boot...
* Reading files needed to boot...

---

### Post by mimetist on 2008-11-11
I have this same problem at boot.

Almost all boot secuence entries are repeated. 

Before this issue I followed this [Howto]("http://ubuntuforums.org/showthread.php?t=565651").

---

### Post by blazemore on 2008-11-11
Oh I think I followed that.
I don't actually think this impacts performance, I think it has something to do with concurrency.

---

