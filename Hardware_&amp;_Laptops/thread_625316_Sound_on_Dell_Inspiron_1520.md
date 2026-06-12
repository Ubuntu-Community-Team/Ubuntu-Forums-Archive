---
title: "Sound on Dell Inspiron 1520"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by bayonetblaha on 2007-11-27
Kubuntu Gutsy on Dell Inspiron 1520 won't make any sound at all.  I have employed the popular suggestion of "sudo apt-get install linux-backports-modules-generic" I see on google everywhere, to no avail. The hardware multimedia buttons function, and I have ensured that both those and the soft mixer are unmuted and turned up. 

"asoundconf list" output:
Names of available sound cards:
Intel


Help!

---

### Post by bayonetblaha on 2007-11-27
solved: select radio button for "front" on mixer

---

### Post by NoPoChris on 2007-12-29
Hi, total noob here.

I also have a 1520 without sound. When I click on the volume control (there's a little speaker with an x in a red box next to it next to the clock display) I get an error message ([screen shot here]("http://www.geocities.com/douchebagchris/ErrorMsg.png"))

I tried "sudo apt-get install linux-backports-modules-generic" and rebooted and got nothing and "asoundconf list" output is nothing. 

I'm running Ubuntu Studio (Gutsy) on Dell Inspiron 1520.

---

### Post by NoPoChris on 2008-01-08
OK, I got the speakers working, kind of. When I log in I hear the login sound, but if I try to use any program that uses sound it freezes and I have to force quit. It's any program that has sound; music players, Firefox, anything, and only when I push the play button. Is there something I can do?

---

### Post by NoPoChris on 2008-01-14
anyone?

---

### Post by linux23dragon on 2008-01-15
> **NoPoChris said:**
> anyone?

Are you using a 32Bit or 64bit OS?

---

### Post by NoPoChris on 2008-01-15
32 bit

---

### Post by Yellow Pasque on 2008-01-15
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
Have you tried adding "options snd-hda-intel model=m44" into the /etc/modprobe.d/alsa-base file.
> 
STAC9205/9254
ref Reference board
dell-m42 Dell (unknown)
dell-m43 Dell Precision
dell-m44 Dell Inspiron

---

### Post by NoPoChris on 2008-02-24
The sound works now, except when I plug in headphones it doesn't mute the speakers. I tried your suggestion, Temujin, but that didn't do it.

---

