---
title: "Update Error"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by be249322 on 2009-05-06
I just upgraded to 9.04 jaunty and now when i try to run the update i get this error...
'E:Type 'good' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I already tried to change source server and no luck...
I am a real big newbie, but i am loving this linux stuff so... Help please...

---

### Post by rannday on 2009-05-06
I have seen a lot of issues with people simply "upgrading" to 9.04.

It might help to download a proper distribution and do a clean install. Meaning, wipe the hard-drive and install Jaunty clean.

Check your download with this:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then either burn to a CD/DVD or create a USB Startup Disk with Ubuntu's USB Startup Disk Creator and install from there.

---

### Post by meindian523 on 2009-05-06
Open /etc/apt/sources.list as administrator:
```

Alt+F2
gksudo gedit /etc/apt/sources.list
Provide password

```
Find the word **good** on the 1st line of the file which opens.Delete the word **good**. Save and Exit.
Try ```
sudo aptitude update
``` again.It should work.

---

### Post by be249322 on 2009-05-06
Perfect fixed!! I find a fresh reload kinda overkill for alot of situations but its often what i have been suggested... But the deletion of the word "good" worked!!

---

### Post by meindian523 on 2009-05-06
Did you use gksudo gedit?

---

### Post by be249322 on 2009-05-07
Yeah i used sudo gedit!

---

### Post by meindian523 on 2009-05-07
```
**gk**sudo gedit
```There's a reason why gk is prepended to sudo.

---

