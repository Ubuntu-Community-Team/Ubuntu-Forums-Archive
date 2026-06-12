---
title: "no sound after upgrading to 9.04"
date: 2009-04-23
forum: Hardware
---

### Post by sgtstukov on 2009-04-23
so i just installed 9.04, and I don't get any sound. when i go into preferences -> sound and hit test i get an error 
"audiotestsrc wave=sine freq=512 !
audioconvert! audioresample! gconfaudiosink:
could not open audio device for playback"

anyone else have this problem, or know of a solution? any help would be much appreciated, thanks!






EDIT:
so i have sound, just not out of my laptop's headphone jack, which is what i was trying to use. has anyone seen this before?

---

### Post by pekmop1024 on 2009-04-23
Same problem with ALC883 (new 9.04 install).

**Upd**: RESOLVED.
1. [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)
2. Strange. The headphone jack output was called 'Surround'. Now all is OK, I'm listening my favorite radio :))).

---

### Post by sgtstukov on 2009-04-23
EDIT: so i want into the codec file, found my model (SigmaTel STAC9205) and tried the things listed below in the /etc/modprobe.d/alsa-base file, but i still have no headphone output... agh this is driving me crazy

---

### Post by tomsa on 2009-04-23
You may be out of luck as a Sigmatel STAC9205 user, see the following bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306755)

Also, here is a thread I started the other day, dealing with the exact same problem:

[http://ubuntuforums.org/showthread.php?t=1131661](http://ubuntuforums.org/showthread.php?t=1131661)

I don't know if there is anyone out there who will be able to get this working.  I may just go back to Hardy or Intrepid until this bug gets fixed.  I kind of need my headphone jack to work.  Sorry to hear you are in the same boat as me.

	](*,)

---

### Post by sgtstukov on 2009-04-24
id would be perfectly willing to downgrade from 9.04, im just not sure how. However, I also had this problem in 8.10, is there any version of ubuntu in which this card is known to work?

---

### Post by tomsa on 2009-04-24
I had it running fine in 8.10- but that was months ago, and I don't remember exactly what I did.  Sorry I can't help you more.  I'll let you know if I see another solution for jaunty though.

---

