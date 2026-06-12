---
title: "External drive locale"
date: 2008-09-15
forum: General Help
---

### Post by Burillo on 2008-09-15
How can i set the default locale for external drive? I mean i insert my USB flash drive and it behaves as en_EN.UTF8. This sucks, 'cos it's really ru_RU.CP1251. I know, 1251 sucks but i need to maintain compatibility between my machines, and since Windoze isn't capable - it should be on ubuntu's side. GNOME manager insists on mounting it as UTF8. If i handmount it via console - i can no longer control the drive with the GNOME manager and need to use console once again. Is there any easy way for this?

---

### Post by Burillo on 2008-09-16
bump

and btw i can't seem to find correct setting for the encoding. 1251? cp1251? cp-1251? win1251? win-1251? windows1251? windows-1251? why are these things inconsistent between various software? and WHY THE HELL aren't they documented?! i'm cool with reading manpages, but it's not even there! so much for user friendliness.

this time i'm pretty much pissed off and forced to boot Windoze just to read those damn files.

---

### Post by Burillo on 2008-09-16
bump

---

### Post by Burillo on 2008-09-17
bump

---

### Post by EmanresuusernamE on 2008-09-17
Are the two language sets between OSs different?  AFAIKnew Linux and Windows didn't use a local to save stuff on a hard drive.  The programs reading/writing data to the drive where the ones concerned with locale.

How are you mounting your drive to change the locale?  If you just mount something in Ubuntu and save the data to it, what does Windows say whe you try to read it?

---

### Post by Burillo on 2008-09-17
my flash drive is vfat so it does matter what locale it uses. Windoze XP AFAIK don't support unicode and writes everything using it's own locales (1251 in my case).

it doesn't matter if the charset used is latin-only. this is not the case.

---

### Post by Burillo on 2008-09-17
if Linux writes in UTF8 - cyrillics become unreadable when using Windows XP (didn't try on Vista though, don't have any). If i try to write with Windows - cyrillics become unreadable in Linux. When i once (succesfully) mounted my drive via console with 1251 encoding (don't remember the actual option i used) - it worked OK but i had no control over that drive in Gnome (e. g. mount/unmount from Nautilus). If i don't fiddle with console - it mounts OK but with UTF8 instead.

---

### Post by EmanresuusernamE on 2008-09-17
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

At the end of the fourth column in your fstab, add the option for your local.  Currently, it slips me on how to get the UUID, but I think should help if you always have it in the same spot.

---

### Post by Burillo on 2008-09-18
btw to ged UUID's type:
```
ls -l /dev/disk/by-uuid/
```

i know how to mount drives in UTF8 (in fact, this is my system locale and Ubuntu does this automagically), but the thing i need is to mount it in WINDOWS encoding (1251 in my case).

i was hoping for some graphical tools (no matter how they hate KDE it's still far superior to GNOME - not just beacuse it has a mountpoint editor that does exactly what i need, but also a bunch of other useful tools). guess every "linux newbie" is destined to end up in console.

---

### Post by EmanresuusernamE on 2008-09-18
Yeah, practically any version of Linux out there is going to put you into a command prompt.  Edit your /etc/fstab and put your UUID in there so that it will mount your drive the way you want it to.  Change the locale for it, and it should automatically mount it in the locale of your choice.

---

