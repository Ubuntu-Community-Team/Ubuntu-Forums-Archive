---
title: "copying files:input/output error"
date: 2005-11-20
forum: Hardware &amp; Laptops
---

### Post by Brando569 on 2005-11-20
so a few days ago i decided to back up all my music onto DVDs cuz i feared my HDD was gonna die, also i wanted to rearrange the partitions on it too. so i burn them all with no problem and had k3b verify then and it all went good. now im trying to copy them back off the dvd and onto the HDD and i keep getting errors. when i try to copy it through the GUI kde tells me every so often that it cant read <filename.mp3> and it says cancel, skip and auto skip. if i hit either of the skips the HDD activity is still the same but the transfer rate drops from about 2-3mb/sec to maybe about 1-200 kb/sec and it stays liek that for a while, sometime it even stalls. after giving up on this i figured hey ill do it through the terminal. so i typed this: sudo cp -R /media/cdrom/* /media/music/*  and everything went well for awhile then the errors started comming back as this:

cp: reading `/media/cdrom/Chevelle/Point #1/06 Anticipation.mp3': input/output error

and i figured it'll only happen once or twice but nah, it kept going on an on. finally i canceled it and i dont know what to do. anybody have a solution to this? :confused:

---

### Post by poptones on 2005-11-20
It's having a hard time reading the DVD. Try wiping it back and forth on your shirt... briskly. 

If it is REALLY having a hard time with it then you can use k3b to copy the DVD to an iso. You can set the options so it will "really, really try" to rip the data before failing. if you can get k3b to make an iso on your drive then you can mount it and copy the data that way.

---

### Post by Brando569 on 2005-11-20
it worked thanks..

---

