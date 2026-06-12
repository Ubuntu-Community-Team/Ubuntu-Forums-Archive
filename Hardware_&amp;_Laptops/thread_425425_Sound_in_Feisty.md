---
title: "Sound in Feisty"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by tmeier on 2007-04-27
I have an IBM X41T tablet PC and recently upgraded to Feisty from Edgy.  I have since lost my sound.  I did a search and ended up at a Bug page for a similar issue and they said these commands tell the story of what is going on.  [https://bugs.launchpad.net/ubuntu/+bug/76876](https://bugs.launchpad.net/ubuntu/+bug/76876)  is the page that talks of this.  Below is what they said should appear.  
$ sudo fuser /dev/dsp
$ sudo lsof /dev/dsp
$ sudo cat /dev/urandom > /dev/dsp
bash: /dev/dsp: Device or resource busy

but mine says permission denied instead of Device or resource busy.  It shows Root and audio group have r/w access to the file.  Do I need to be part of the audio group?  

It is an Intel 810 chipset and is listed as an ICH6 AC97 sound card.  If you need more info please let me know.

Thomas

---

### Post by K0LO on 2007-04-28
tmeier:

I'm currently trying to figure this one out also. I've noted that you can restore sound by suspending to ram and then waking. Upon re-awakening, the sound works again.

---

### Post by tmeier on 2007-05-01
I bit the bullet and just backed up my home directory and reinstalled Feisty from the alternate cd and now I have sound.  I repartioned so my home directory is on its own partition, now if I have to reinstall no big deal.

Thomas

---

### Post by K0LO on 2007-06-04
This fix worked:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96230/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96230/comments/27)

---

