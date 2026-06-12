---
title: "Nvidia issues with upgrade to 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by dgould0622 on 2010-05-03
I had no issues with my video drivers in 9.10, with the recent update to 10.04, none of my 3d graphics from compiz are working. I set the effects to extra and all it does is enable my window border. Every time i close out of it, it sets itself back to none.
When i look under system - administration - hardware drivers, it says "no propriatary drivers are in use on this system. Also, everytime i reboot my computer my resolution is all messed up and my window decorations are gone and i have to hit "extra" under visual effects to reset it. So i would like to know why my 3d graphics arent workign and why my nvidia drivers dont show up and how can i upgrade them?

---

### Post by dgould0622 on 2010-05-05
bump. anyone else having realted issues? now its telling me i have to run it in lower resolution because nvidia needs to be upgraded. how do i go about upgrading nvidia?

---

### Post by andretardif on 2010-05-06
Very good question, I'm having the exact same problem. I have not found a fix as of yet.

---

### Post by tad1073 on 2010-05-06
try```
sudo nvidia-xconfig
```

---

### Post by andretardif on 2010-05-06
That did not work same result on startup, I am wondering where the "lower resolution" post or doc came from and how that would impact settings. It has to be pointing to a wrong setting on startup I'm just not sure where.

---

### Post by DatOne on 2010-06-14
I am having the same problem. Any one have a fix?

---

### Post by NewDisciple on 2010-06-14
**Here is another thread [http://forumubuntusoftware.info/viewtopic.php?f=69&t=4749]("http://forumubuntusoftware.info/viewtopic.php?f=69&t=4749")**

---

### Post by ankit singh on 2010-06-14
This message also haunted me after i upgraded to lucid. I removed the installed driver and used synaptic to have the upgraded one.

---

