---
title: "Not all RAM in use - how to get you full RAM ??"
date: 2008-09-25
forum: General Help
---

### Post by StevenRoose3 on 2008-09-25
Hi,

I've installed Ubuntu 8.04 just at the release day and updated it normal, and I see now in the System Monitor that Ubuntu just recognize 438.7 MB of the 512 MB that it should be.

Does anyone knows the reason why Ubuntu don't uses it all, and is it fixable without having to re-install Ubuntu. (what wouldn't be a thàt huge problem cuz the update is coming soon)

thanks in advance,
Steven

---

### Post by jualin on 2008-09-25
What do you mean with "does't use it all"?
Usually your operating system doesn't use all the amount of Ram that you have. For instance I have 1 GB of RAM and in system monitor I am using about 400 mb out of 1 GB. Now if what you meant was that Ubuntu didn't recognize the full amount of RAM you have, for instance it says that you are using 400mb out of 432 mb, then you should check that you don't have an integrated graphics card, since those types of graphic cards utilize a part of your RAM to work. Also you can check on Windows if you have the same amount of RAM that Ubuntu is reporting. Hope this helps!

---

### Post by StevenRoose3 on 2008-09-25
it recognizes just 438 out of 512, is this rest possible fr a ATI graphic card on Toshiba? dunno anything about graphic cards.

Long time ago I runned CCleaner in Windows, cuz that app shows the RAM too, but i think it actually showed 512, i'm not sure, but i really think it was more than 438.

---

### Post by jualin on 2008-09-25
Usually most video cards on laptops are IGP (integrated graphic processors) which consume part of you RAM to work. My Compaq laptop works that way. You can always check on Windows for the amount of RAM that you have. Just boot on Windows and right click on My Computer (Computer if Vista) and click on properties, and the amount of RAM should be listed. Also you can use the Direct X Diagnostic Utility by clicking on Start, Run, and typing dxdiag and then pressing "ok". Good luck!

---

### Post by StevenRoose3 on 2008-09-25
Thanks!
If the RAM amount in windows is more, should i re-contact u then here?

I will check maybe tomorrow, gonna sleep now

---

### Post by lisati on 2008-09-25
Ditto with the suggestion that possibly it's somehow connected with the video card - my Compaq desktop does that too. I haven't taken too much notice on my laptop, since I use it mostly for internet-related stuff that isn't too memory intensive. You might be able to get some clues during boot-up from the diagnostics that some machines can display - on my Toshiba laptop, I press "Esc" while the Toshiba splash screen is showing to display them.

---

### Post by jualin on 2008-09-25
> **StevenRoose3 said:**
> Thanks!
If the RAM amount in windows is more, should i re-contact u then here?

I will check maybe tomorrow, gonna sleep now

Of course keep us posted! Good nite!

---

### Post by ryanhaigh on 2008-09-25
73.3MB of RAM seems like a very strange amount for a graphics card to be using and the fact that windows is reporting the full amount indicates, to me at least, that this is not the issue.

Perhaps a segment of your ram is faulty? I know windows will happily try and run with bad ram until you use that segment and you get random stange issues.

Try running memtest from the livecd (or possibly grub) and see how much ram it says you have and if any of it has errors.

---

### Post by dlm4849 on 2008-09-25
I was wondering this too. I have 2 - 2 gig sticks in my laptop with dedicated video and it only reports 3.86 gigs.

---

### Post by y@w on 2008-09-25
Every once in a while you will find a BIOS that you can tweak the amount of memory that the integrated video card uses. In this case you can go into the BIOS and see or it may show you while it POSTs as well.

---

### Post by ryanhaigh on 2008-09-25
> **dlm4849 said:**
> I was wondering this too. I have 2 - 2 gig sticks in my laptop with dedicated video and it only reports 3.86 gigs.

This is probably a separate issue associated with a 32-bit operating system not being able to address a full 4GB of ram, search the forums/google and you should find plenty of info. I believe there are patches to enable 32-bit linux to use 4GB or you can just install the 64 bit version of ubuntu, but that may have other implications.

---

### Post by bingoUV on 2008-09-25
StevenRoose3, could you post the output of the following ?
```

cat /proc/meminfo

```

---

### Post by dlm4849 on 2008-09-27
> **ryanhaigh said:**
> This is probably a separate issue associated with a 32-bit operating system not being able to address a full 4GB of ram, search the forums/google and you should find plenty of info. I believe there are patches to enable 32-bit linux to use 4GB or you can just install the 64 bit version of ubuntu, but that may have other implications.

I am using the 64 bit version already.

---

### Post by dcstar on 2008-09-28
People need to understand the difference between MBs and MiBs, and GBs and GiBs.

---

### Post by dlm4849 on 2008-09-28
I never noticed that the measurments were MiB and GiB and not MB and GB. Thanks for pointing that out. That accounts for the discrepency (in my case at least.)

---

### Post by cariboo on 2008-09-28
I've got 2Gb of ram and an integrated video card i get this when i run:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1976       1442        534          0         82        693
-/+ buffers/cache:        666       1310
Swap:         5530          0       5530
```

Yet when I check Nvidia X Server Setting It tells me my integrated video card has 256MB of ram. See attached screen shot.

---

