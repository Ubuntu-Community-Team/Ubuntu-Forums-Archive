---
title: "Harddrive Broken?"
date: 2009-05-04
forum: Hardware
---

### Post by Skootle on 2009-05-04
Hello,

I have a Dell Inspiron 1520 and I think  my harddrive is broken but, before I go out and buy a new one, I wanted to ask you guys just to make sure it was actually the harddrive and not something else.

A couple of weeks ago, my laptop dropped (while turned on) from about 12 inches. From then onwards, I can boot my computer and whatnot, but sometimes randomly it'll completely freeze at some point (after having booted) so I have to forcefully shut it down, and it will also seemingly randomly "check" my harddrives in one of two ways:

 - Ubuntu Logo shows up and starts booting > ubuntu logo still displays but progress bar changes to "Unclean Shutdown, checking drives..." > get thrown into terminal about half way through > "Press Cntrl-D to resume boot normally".

 - Sometimes, it will go directly from GRUB to a black screen with white text showing me a ton of errors on my harddrive and then throw me to the aforementioned terminal. 

After both cases, an "fsck -v" fixes various problems and, after a reboot, seems to work fine. However, the whole thing has happened 4 or 5 times at least in the past week.



This to me clearly seems like a harddrive problem but since I'm not an expert, I wanted to check with you guys. To fix the problem, would I only need to install any 2.5" SATA HDD?

Thanks :)

PS: Using Ubuntu 9.04 but don't think that matters too much...

---

### Post by scott1541 on 2009-05-04
One time i put my laptop on a table and it slid onto a chair and then dropped onto the floor from about 2 feet onto a tiled surface and the only thing that changed was that the dvd drive made some strange sounds for a week or so, after that it was fine and still works and i have a Serial ATA drive the same as you. 

I know you won't find this much help, i thought i would just share my story:)

---

### Post by Skootle on 2009-05-04
I know, it's a bit strange: when I started up my laptop to write the first post, it did what I described above. Now I turned it on again and no problems whatsoever.
Oh, I forgot to mention that at first I thought it  might just be corrupted data, but I formatted and reinstalled.

---

### Post by Wydarr on 2009-05-04
Same here, dropped a Dell Inspiron 1501 from about 2'5" - 72cm (went and measured the table :) ) while it was running, cracked the case (one of the corners is missing completely, but it still runs seamlessly (or so it seems). 
The only two things that come to my mind, is check to see if the RAM is still in place (in case you have access to it) and if the HDD is still secure and firmly in place. I know it's not much, but other than running a full scan with badblocks on it, or referring it for servicing, it's all I can think of. 
Hope you can fix this. Best of luck.

---

### Post by Skootle on 2009-05-04
Thanks :)

When I get back home I'll open it up and make sure the HDD is connected, then I'll do BadBlocks and if that fails, I'll just buy a new HDD.

Thanks though :)

---

### Post by rush_ad on 2009-05-04
> **Skootle said:**
> Thanks :)

When I get back home I'll open it up and make sure the HDD is connected, then I'll do BadBlocks and if that fails, I'll just buy a new HDD.

Thanks though :)

i have a very similar problem however i never dropped my laptop. let me know if it is in fact a broken hard drive or any other solution fixed.

only difference is that when i had vista on it (a week ago) laptop was working fine. right after i installed linux last week, i started having these problems.

---

### Post by Skootle on 2009-05-04
> **rush_ad said:**
> i have a very similar problem however i never dropped my laptop. let me know if it is in fact a broken hard drive or any other solution fixed.

only difference is that when i had vista on it (a week ago) laptop was working fine. right after i installed linux last week, i started having these problems.

OK, once I check this out, I'll let you know.

---

### Post by Skootle on 2009-05-04
> **rush_ad said:**
> i have a very similar problem however i never dropped my laptop. let me know if it is in fact a broken hard drive or any other solution fixed.

only difference is that when i had vista on it (a week ago) laptop was working fine. right after i installed linux last week, i started having these problems.

Ok, so I loaded up Parted Magic (LiveCD) and it automatically diagnosed my HDD, concluding that it was not 'healthy' and, from what I read up on, that is not a good sign. I used Superblocks from there, but to no avail (no error message at the end, but still have the same problem) and then fsck -v, but again, no luck.

Turns out my superblock is corrupted and I can't find the backups; I can still get data from it, but it seems unusable (at least very unstable), so I decided to buy a new hdd and get it over with.

---

### Post by rush_ad on 2009-05-05
> **Skootle said:**
> Ok, so I loaded up Parted Magic (LiveCD) and it automatically diagnosed my HDD, concluding that it was not 'healthy' and, from what I read up on, that is not a good sign. I used Superblocks from there, but to no avail (no error message at the end, but still have the same problem) and then fsck -v, but again, no luck.

Turns out my superblock is corrupted and I can't find the backups; I can still get data from it, but it seems unusable (at least very unstable), so I decided to buy a new hdd and get it over with.

i don't think it makes sense for me spend more money on this old laptop.

since i had put in new RAM chip (2gb) i decided to run memtest on it. it turns out, i got 376 errors in hour and a half. 

Do you think bad ram has anything to do with the problem? also, how many memtest errors on a 2gb stick is bad?

---

### Post by Skootle on 2009-05-05
I don't think I'm the  best person to advise you, but as Wydarr said, it could be the RAM. Right now I'm "living" on the Ubuntu LiveCD with no problems (it's understandbly a bit slow, but nothing major) so I really doubt in my case it's the RAM. Maybe you should try using the LiveCD for a while and see what happens?

Sorry I can't offer specific help, but maybe someone else can

---

