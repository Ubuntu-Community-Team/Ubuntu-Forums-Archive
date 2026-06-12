---
title: "Dell e6000 media buttons"
date: 2006-11-28
forum: Hardware &amp; Laptops
---

### Post by Shon on 2006-11-28
I recently partitioned my hard drive into windows XP and kubuntu (dapper).  Kubuntu is working great (I have yet had a reason to use windows), however I cannot get the media buttons on the front of my Dell Inspiron 6000 to work at all, in or outside any media program.  I've tried the suggestions of setting them as global shortcuts in Amarok but that hasen't worked, and I can't seem to find any drivers that might help.  Anyone not had these buttons work out of the box and gotten them to work (at least in amarok)?  Thanks!

---

### Post by KingBahamut on 2006-11-28
apt-get install hotkey-setup , memory serving correctly.

---

### Post by Shon on 2006-11-28
I tried that, and got this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any thoughts?

---

### Post by KingBahamut on 2006-11-28
gerf. 

sudo apt-get install hotkey-setup 

sorry.

---

### Post by rbprogrammer on 2006-11-28
i had that same problem with the same laptop, i use keytouch.  it is in synaptic/adept but you might have to enable universe and/or multiverse
 to download it.

hope that program helps you....

---

### Post by Shon on 2006-11-28
The hotkey program doesn't seem to work, unless there's somethign other than installing it I'm supposed to do.  I also ran into trouble installing KeyTouch.  I'm way too inexperienced to work with the text based interface in Kate, and can't seem to find any GUI of any sort...Thanks for the suggestions though!

---

