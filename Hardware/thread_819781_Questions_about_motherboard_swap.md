---
title: "Questions about motherboard swap"
date: 2008-06-05
forum: Hardware
---

### Post by gyzer on 2008-06-05
I am currently having hardware problems (or at least I'm 95% sure its just hardware problems) with my computer that is running hardy. I belive my problem has to do with the motherboard and I had some questions:

If I'm swapping out an entirly different type of motherboard, will Ubuntu detect the new hardware and load those drivers accordingly or will it be like windows where it will error out and only a fresh install of the os will make it all work?

Is there anyway to make an image of my hard drive that hardy is installed on? If there is what programs are best to use?

If I can't do an image, is there a way to backup different settings and installed programs so after I do a new install of hardy it will be as painless as possible to get back to my current state of all my settings and installed programs?

---

### Post by tamoneya on 2008-06-05
you can give it a try but I am not optimistic.  It is much more likely than windows which has a 0% chance of succeeding but I wouldnt bet on it.  Here is how I would solve the problem:
1) use remastersys to make a custom ISO so that your programs will be saved
2) back up ~ so that your preferences and files will be saved
3) install from remastersys custom ISO
4) replace ~

---

### Post by thideras on 2008-06-05
If it is the same motherboard, you should be ok.  If you are switching chipsets, backup first.

I went from a eVGA 780i to a P5K Premium without reinstalling.  It got to the login screen and hard-locked.  Restarting caused a kernel panic.  Ended up wiping anyway.

---

### Post by gyzer on 2008-06-05
So pretty much I just remastersys and save the iso on my secondary non-boot hard drive? 
 
How do you then reinstall it after switching the mobo?

---

### Post by tamoneya on 2008-06-05
you burn the iso to a cd/dvd.  Then you use that custom cd/dvd to install instead of the normal ubuntu CD.

---

### Post by gyzer on 2008-06-06
so I back up my home directory to a secondary hard drive or something, and then do the remastersys iso, and use that new cd to install Ubuntu over again, and then I just copy back over my home directory? 
 
Are there any other directories that I should backup because of settings?
 
So doing this will back up my installed themes and such?

---

