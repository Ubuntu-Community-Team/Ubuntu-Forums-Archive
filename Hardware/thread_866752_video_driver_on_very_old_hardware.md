---
title: "video driver on very old hardware"
date: 2008-07-22
forum: Hardware
---

### Post by bro on 2008-07-22
I just installed Xubuntu on a very old laptop with a VIA Samuel 2 processor. I don't I have the proper display drivers installed though. It just says 'configured video device' in xorg.conf. 
How do I find out (in Xubuntu) what kind of video hardware I have and then how do I install proper drivers (if any available)?

---

### Post by overdrank on 2008-07-22
> **bro said:**
> I just installed Xubuntu on a very old laptop with a VIA Samuel 2 processor. I don't I have the proper display drivers installed though. It just says 'configured video device' in xorg.conf. 
How do I find out (in Xubuntu) what kind of video hardware I have and then how do I install proper drivers (if any available)?

Hi and you may try the command ```
gksu displayconfig-gtk
``` there you can view the driver being used and configure your system.

---

### Post by bro on 2008-07-22
Thanks. It says that I have a Sis630 card. How/where do I find a driver for this? Any clue?

---

### Post by bro on 2008-07-22
On [this thread]("http://forum.ubuntu-fr.org/viewtopic.php?id=136300") there is talking in French that the Vesa writer should work? At least that's my guess, I don't really speak french... If so, how could I enable that exactly?

---

