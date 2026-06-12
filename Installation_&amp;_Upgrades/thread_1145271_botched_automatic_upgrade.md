---
title: "botched automatic upgrade"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by sunbound on 2009-05-01
I recently put my linux PC back into my rach after it being pulled out for a few months. After booting, it let me know that their was an upgrade available. I opted for the automated upgrade, (didnt even think about backing it up. After it started to download, i walked away for a few hours, came back and found a frozen desktop... but it was like the resolution was way off, and i couldnt do anything. 

I manually re-booted the PC, and now it wont even load. 

It will post, but shortly after, all i see is a blinking curser at the top left of the moniter. Ive let it sit for a few hours to see if it would load, and nothing. 

I would glady do a fresh install, but i would like to keep most of the files I have on the messed up install. 

I have the new 9.04, not sure what the old version was, but it was current a few months ago. 

I would love to be able to just copy everything on the hard drive to my external NTFS drive, but im new to this, and dont know how to get that far. I've tried a few things, but they havnt worked so far. 

If i could either copy everything to my external HDD, or somehow just repair the install I have so its usable, then copy the stuff over myself...

any help would be greatly appreciated. 

Jon

---

### Post by CMJ Tech on 2009-05-01
Are you able to boot the live CD?

---

### Post by sunbound on 2009-05-03
Yes, I'm able to boot the LiveCD, and it works fine, but i cant find my HDD. It can see my external NTFS drive, but i havnt tried to write to it yet. 

Thanks

Jon

---

### Post by sunbound on 2009-05-04
So far here is what I have 

I can boot to the liveCD
I can read and write to my external NTFS terabyte HDD
I still cannot view the internal IDE HDD. I even tried using a USB IDE adapter, thinking it might "force" a mount, or ask me what i want to do with it, but it did nothing. when i plug in my WD external, it mounts it automatically. 

the IDE is formatted with EXT3, i think. 

Thanks

Jon

---

### Post by CMJ Tech on 2009-05-04
I am still a novice with linux, but I had a similar problem with my system when I tried to upgrade my system from 8.10 to 9.04.  After doing the upgrade to 9.04 my system would not boot.  I was able to run the 9.04 live cd, but was not able to install.  What I ended up doing was using an old 7.10 live cd to install ubuntu on my system and then upgraded to 8.04.  
I was wondering if that might work for you.  Try installing an older version, but instead of using the entire drive for the install, have it partition the drive leaving your installation that will not boot intact.  
If that works, then you should be able to see your files you need to retrieve.

---

