---
title: "Installation problem"
date: 2005-11-25
forum: General Help
---

### Post by rikard_grankvist on 2005-11-25
I have a dual boot windows/mandriva linux installation, and I wish to switch from mandriva to ubuntu. I started the installer and I got past the partitioning section. I deleted my current linux partitions to get a clean slate. At the next step ("install base system"), it gives an error message "cannot complete installation step". I use the mandriva/LILO bootloader, so I tried jumping straight to the "install boot loader step", because it thought that was the problem. I got the same error. Any tips on how to get my ubuntu installed? I'm anxious to switch from mandriva.

---

### Post by Schmots on 2005-11-25
Does it try to load any of the files?  Did you maybe burn a bad disk?

---

### Post by rikard_grankvist on 2005-11-25
The disk is one of those you can have sent to you, e.g. an official disk with logo and all. So it'd b weird if it's bad.

I suppose it loaded some files before it got the error, at that particular installation step, but it flips away too fast to see. I think there was something in the error message about a log. I'll try again to see if I can produce one to post here.

---

### Post by linbetwin on 2005-11-25
I suppose you've received at least 5 discs. Try another one. It seems you are not the only one reporting a corrupt official CD. There is nothing weird about that. I am only sorry for Cannonical, because it's their money that's wasted. I for one never look a gift horse in the mouth.

---

### Post by rikard_grankvist on 2005-11-25
I only have 2 CD's, one installation disk and one live CD. I suppose this is a lighter version (it's 5.10 though).

---

### Post by Bachstelze on 2005-11-25
The Live CD is used mainly for demonstration purposes, it allows you to run Ubuntu without modifying anything on the HD.

---

### Post by rikard_grankvist on 2005-11-25
Well yeah, I *know* that. I'm not a complete newbie. I'm just saying that there weren't 5 discs as he suggested, really just one.

---

### Post by rikard_grankvist on 2005-11-26
Ok. I've tried it again, and it says:

"Debootstrap program has exited with an error (return value 1).

Check /target/var/log/bootstrap.log for details."

However, when I go back to windows and check, there is no /var/log/bootstrap.log. After that error message, the one I already described appears, and then I'm sent to the list with installation steps.

I've tried formatting the boot record, but it didn't work. Exact same error appeared. Anybody have an idea as to what it might be?

---

### Post by Schmots on 2005-11-26
When he said 5 cds, he figured you ordered them, not got one from a friend.  and what it is.. is you have a bad cd, sorry.

---

