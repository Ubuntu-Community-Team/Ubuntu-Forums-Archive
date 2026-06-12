---
title: "Install 9.10 from iso and keep settings"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by dkknight593 on 2009-10-05
Something happened on my linux 9.04 and after loading I get a blank screen.  Ubuntu is running because I can log in and hear the sound in the background.  I am using the flgrx driver but don't think it's a driver problem since it was working long time.

So if I install 9.10 from iso.  Will I be able to keep my old settings?

---

### Post by slakkie on 2009-10-05
Personal settings of different applications? If you have a seperate homedir (/home), yes. If you don't have a seperate homedir, no.

System wide settings (/etc) no, will be overwritten by a new install.


And please, don't install 9.10. Questions like these should not be asked by beta testers.

---

### Post by mikewhatever on 2009-10-05
You will, but only if you have a separate home partition. It usually requires manual formatting to set it up, so that if you don't know, you probably don't have it. On the other hand, have you tries fixX option from the recovery mode?

---

### Post by dkknight593 on 2009-10-05
I already have seperate boot and home partitions.

I'm thinking though I will lose all my installed programs which might be OK.

---

### Post by mikewhatever on 2009-10-05
> **dkknight593 said:**
> I already have seperate boot and home partitions.

I'm thinking though I will lose all my installed programs which might be OK.

Yes, you will, but you'll still retain the settings, just don't format the home partition. You'll have to use the manual partitioning options to specify the mount points, /, /home and /boot.

---

