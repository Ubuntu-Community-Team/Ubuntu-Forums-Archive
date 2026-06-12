---
title: "Hp G61-451EE sound problem"
date: 2010-04-05
forum: Hardware
---

### Post by ahmicro on 2010-04-05
Hello every one
I get a new laptop hp [G61-451EE]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01963550&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=4105278#jumptocontent")
I installed Ubuntu 9.10 but i can't hear any sound. is ther any problem with the driver 
*system is up to date
* sound works well on windows 7
Thanks

---

### Post by ahmicro on 2010-04-06
Any help guys!!

---

### Post by ahmicro on 2010-04-11
Thanks open source community, no reply !!

---

### Post by Manyette on 2010-04-11
I'm not sure this will help you, but I have a G71, and the fix for me was in the following thread.  Good luck.

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/91675)

Don

---

### Post by ahmicro on 2010-04-15
Not working for me 
Please !!

---

### Post by Manyette on 2010-04-15
If the end of your alsa-base.conf file looks like the following, then the problem is something other than the "routine" HP G60/70 fix, and I can't be of any help.  But perhaps someone else more knowledgeable than I will see this and jump in here.

=======================================================
ADD THIS TO BOTTOM OF the alsa-base.conf FILE AND SAVE
=======================================================

# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1

=======================================================

Anyone else have an idea?

Don

---

