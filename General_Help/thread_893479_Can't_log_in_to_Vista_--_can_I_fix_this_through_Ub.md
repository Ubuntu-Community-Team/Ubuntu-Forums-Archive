---
title: "Can't log in to Vista -- can I fix this through Ubuntu? (ntuser.dat help)"
date: 2008-08-18
forum: General Help
---

### Post by rabidg00se on 2008-08-18
Hey all, I realize this is a Linux forum, but I also know that a lot of you have some experience with Windows installs (and besides, this is the best place I know to ask this question if I don't feel like getting flamed), so maybe you can help me.

A few days ago my install of Vista Ultimate stopped letting me log in. The only reason I can think of for this is that I've been using Ubuntu 8.04 a lot lately, including accessing music and other files on the Windows partition. Anyway, I got the error "C:/Users/Maximus Prime is corrupt and unreadable. Run the CHKDSK utility." or something similar, and was brought to a temp profile. This had happened before (although never to my user folder), so I ran CHKDSK twice with no errors either time, but it still didn't work. I Googled for some help and found [this]("http://cherrybyte.blogspot.com/2007/07/fixing-user-profiles-in-vista.html"). I tried the registry fixes recommended in there (the RefState value was at 32768, and both my regular and admin accounts were renamed .bak), in both the temp account and the "secret" admin account mentioned in one of the comments. No dice.

Now, I realized that the volume automounts just fine under Ubuntu, including files that are in the supposedly corrupt, unreadable user folder. If you take a look at the screenshot, you'll see that ntuser.dat (which is apparently the important file here) has quite a number of incarnations. I don't know which of them are supposed to be there, and I certainly don't want to go messing around in them without some advice.

Any ideas?

(The screenshot attached is of the folder C:/Users/Maximus Prime, the only account I use regularly)

---

### Post by Sycron on 2008-08-18
Did you tried logging in safe mode?

---

### Post by Archmage on 2008-08-18
Or the recovery mode from the CD. There you can start the chcks.

But I doubt that this has something to do with Ubuntu. But it might be possibile that your harddrive is slowly dying and producing errors.

---

### Post by rabidg00se on 2008-08-18
I just tried safe mode, I can't log into my regular profile. I also tried making the changes to the registry again, but again they didn't work. I don't have the CD here (although I *do* have it, I promise), but how would that CHKDSK be any different from the one the system can run without it?

I hope the drive's not dying, the computer is barely seven months old.

I'm not sure what I expect Ubuntu to be able to do, except show me that there are so many ntuser.dat files that I can't get to through Windows at the moment. Maybe somebody with experience with Vista/XP eating profiles can help me edit or at least make sense of them?

---

### Post by rabidg00se on 2008-08-18
Bump, sorry if it's "impolite"

---

### Post by Sycron on 2008-08-21
Windows is like a mad dog... You'll never know when it's gonna give you a nice BSoD on ya face, but surely will be when you wont expect.

---

