---
title: "can you help me log back in to XP?"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-03-08
last two days I installed XP, next day Ubuntu
on the HDD with 3 partitions, two NTFS and third just a RAW with manualy pointing to that place
both OS are [there]("http://ubuntuforums.org/showthread.php?t=1090013"), 
Ubuntu updated fully, and since than
when restart the boot selection won't take me to the XP boot, just an endless circle.
have to get back to pickup my emails, not fun sitting at home w/o job.
shall I need a third party program? to install from inside Ubuntu what can make the initial boot switch automatically? 
I'm not really educated with these typings beside using PC for maybe 20 yrs

---

### Post by zvacet on 2009-03-08
Insead of 

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1

let it look 

title      Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

Save and close.Reboot and you should be able to boot in Windows.

---

### Post by attilab on 2009-03-08
where and how to make these changes?
pls

---

### Post by zvacet on 2009-03-08
In terminal type
 
```
gksudo gedit /boot/grub/menu.lst
```

and then just replace your lines (you will find them at the bottom of the page) with ones I posted you.Save file and close it,and reboot.

---

### Post by attilab on 2009-03-08
did the change, restart,
on the boot selection screen I select the XP command, 
but just blinks, for a portion of the second want to go somewhere but gets back to the selection, in the circle.
what is a work-arround?

---

### Post by attilab on 2009-03-08
thanks all for a great effort helping me with this,
unfortunatelly time is not on my side with this dual boot, 3 days Im trying to make it work,
I feel that I am very close with this, but
tomorow is a work day, I need to get back to my XP
I guess I shall hit the Fdisk soon,
Im going to read one more time how to partition for future installation and I have to go...everybody pissed around me not paying time to family.

---

