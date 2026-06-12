---
title: "No room at the Inn"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Swagman on 2009-05-09
My mate brought his laptop round my place today to do some updates. He has no internet connection so I do it all here for him.

I persuaded him to try Ubuntu a while back, installing via wubi within XP.
He likes it a lot saying it is much easier to use.

Sounds good doesn't it.

Updates rarely go well though usually freezing the machine and then having to dpkg--configure -a to sort em out, this time being no exception.

So I decide to dist upgrade to Jaunty. Naturally it b0rked the update so I choose another kernal at grub and save out all his gubbins and decide to bite the bullet and dual boot proper.

Boot into windows and uninstall Ubuntu. Download 9:04 on my machine and burn ISO (i386).... Here we gooOOOooooo.

Install detects other os and suggest resize to give Ubuntu 29 gigs. That should be ok for him.

Install... Everything Hunky Dory.
Reboot ... Luvverley.
Fire up Update Manager and......[**W T F**]( http://www.upload3r.com/serve/090509/1241901369.jpeg)

You cannot be serious? /McEnroe

Check Home **4** ... YES **FOUR** mb free space !!
I just don't believe it. Now I've got to go into windows... hope FixMBR works without the XP disk (he's got that at home)
Blow Ubuntu off the drive.. Resize the bloody partition again and reinstall via Wubi.

The mind boggles.

I bet that cretinous wait whilst "Activating Swap" error hasn't been cured either.

Groan.

mutters.. Why can't I just win the lotto big time and buy really kewl stuff.

---

### Post by Partyboi2 on 2009-05-09
Hi, if there is a mistake with the size of your /home partition you can boot a live cd and use gparted to increase the size of your /home partition.

---

### Post by Swagman on 2009-05-10
Hi.. Thanks for the reply.

New day.. New train of thought.. heat of the moment etc !!

I successfully shrank the XP C:\ partition down and windows still works ok.. So now I'm going to have a play in GParted to see if I can expand Ubuntu.

At worst I can just delete the partitions and reinstall Ubuntu.

---

