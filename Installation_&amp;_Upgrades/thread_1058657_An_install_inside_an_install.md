---
title: "An install inside an install?"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Lanky Juggler on 2009-02-03
Backstory: I came home this evening to find that my ubuntu didn't want to boot anymore, with grub errors, and also my linux install itself kind of weird. I've since managed to get things running again, but it's been messy because I'm rusty on fixing things (yay, things not breaking in a while!).  Anyways, from way back when, I have 2 partitions of interest to this thread: 5 gigs for /, and a much larger partition for /home, where all my real files go.  This was supposed to lend some safety, should such a thing as what just happened ever happen, so hooray!

But I messed up the first reinstall, and I ended up with an install of 8.04 which had no login name or password, so you couldn't actually DO anything with it.  I managed to install 8.04 again, overwriting the 5 gig partition where my working 8.10 used to live, and now everything boots just fine! I've re-updated the usable install to 8.10 and all of my settings/programs/etc that were stored in my larger partition are still there! Success!

BUT! Now I have this ghost install, taking up space and being confusing. I would really appreciate it if someone had a suggestion for getting rid of it, just for the sake of organization/space.

1. In Grub, underneath my 8.10 install is my wonky 8.04 install.  I know how to delete it from the grub listing quite easily, but can I delete the install itself of the defunct OS completely? Grub lists it as being contained in SD1, my 60 gig partition (the one for files, not the smaller 5 gig one).

2, which possibly complicates and/or explain is explained by 1.  I have recently noticed that, since this craziness occured, my home folder ... contains another home folder, not to mention var, lib, usr, and the like.

I'll try to explain better: Topmost in my file organization is a set of folders: usr, var, home, the usual. WITHIN that /home, is another listing of var, opt, etc, along with the /sam folder that should be there and goes to my files.  The /home/home folder is empty.  Can I just delete this "subset" of folders, since they don't seem immediately connected to the usual /home/sam path of things? Is that my ghost install?

Thanks in advance, for any thoughts or tips.  I'm kind of stumped.

---

### Post by lha on 2009-02-08
It seems to me that you are on the right track. However, before you remove the parts that you think are you ghost installation, back them up. If you remove something that you shouldn't remove, you can get it back easily.

---

### Post by Lanky Juggler on 2009-02-08
Thanks for the advice!  In retrospect, backing it up would have been rather intelligent.

I actually ended up figuring it out by making a very quick shell file with an echo command, and putting it only one of the two following: /usr/bin/ and /home/usr/bin (the weirdo folder).  I could execute the script from my terminal if it was in /usr/bin, as expected, but not if it was only in the other folder, so I figured it was the weird twin-install.

Case Closed.

---

