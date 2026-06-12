---
title: "NVIDIA Drivers &amp; unable to connect to X server"
date: 2011-07-24
forum: Hardware
---

### Post by Blitzskee on 2011-07-24
Hi guys, I'm a Ubuntu newbie but really excited about getting into using it, I've tried a few times in the past but never stuck to it but I'm really going to give it a go this time.

I have a problem, if someone wouldn't mind helping me out

I have a Dell Inspiron 15R laptop running Ubuntu 11.04, it was unable to run Unity I thought the gfx card needed updating so I downloaded the latest drivers from NVIDIA (My card is 525M, driver I downloaded was a file named "NVIDIA-Linux-x86-275.21.run")

Anyways after installation I had to start the X server again because I had to disable it to install the drivers.  When I attempted to do this I had these errors:

Fatal server error: no screens found
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

Any help would be appreciated =)

---

### Post by realzippy on 2011-07-24
Isn't that an OPTIMUS laptop ?
If so,the trouble is explained [here]("http://ubuntuforums.org/showthread.php?p=10304516#post10304516").

---

### Post by Blitzskee on 2011-07-24
Thank you very much I guess that explains everything as it is Optimus...

However I'm not sure why Unity wouldn't start and I'm forced to run classic. If that article is correct in saying my integrated whatever should run everything fine :(

---

### Post by realzippy on 2011-07-24
Yes,unity should work on intel integrated graphics.Here it runs fine,
unfortunately I cannot stand the Unity Desktop,so I run GnomeClassic.
Set this thread as solved and create a new one (after searching the forum;
quite sure I stumbled upon this problem here in the past..)
Good luck!

---

### Post by Blitzskee on 2011-07-24
thank u very much ...although I am unsure how to change it to solved?

---

### Post by realzippy on 2011-07-25
(Thread Tools),right upper corner,red letters.

---

