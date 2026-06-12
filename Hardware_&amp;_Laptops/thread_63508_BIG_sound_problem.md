---
title: "BIG sound problem"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by da_unruled on 2005-09-08
Well.... Sound used to partially work for me in ubuntu... games would crash because they couldn't initialise, but for the rest, OS sounds, xmms, etc etc worked.
Now somethings happened and not even one of the sound systems works. (before only 1 or 2 of them worked).
They all say cannot initialise pipeline.

please can you help me fix this?
thanks

---

### Post by swamytk on 2005-09-08
Try installing libesd-alsa package. I got it solved for my problem like this.

---

### Post by da_unruled on 2005-09-09
[QUOTE=swamytk]Try installing libesd-alsa package. I got it solved for my problem like this.[/QUOTE]
 how would I do that?
sudo apt-get install libesd-alsa ? it says package not found..

thanks

edit: well I tried to just reinstall alsa and install libesd, but it still gives 'failed to construct pipeline' no matter which multimedia system I choose.  :???:

---

### Post by swamytk on 2005-09-10
You have to install libesd-also0 package. If you are installing, you can't have libesd0 package. So you uninstall the libesd0 package. (Anyway synaptic takes care of this dependency)

---

### Post by Steve1961 on 2005-09-10
The posts below helped me to get things up and running on four different PCs.  For three boxes the first link worked, and for the fourth the second link worked.

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)

[http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf+alsa](http://ubuntuforums.org/showthread.php?t=32063&highlight=gandalf+alsa)

---

