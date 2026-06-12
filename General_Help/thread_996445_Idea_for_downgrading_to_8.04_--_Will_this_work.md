---
title: "Idea for downgrading to 8.04 -- Will this work?"
date: 2008-11-28
forum: General Help
---

### Post by EvilRobotDrew on 2008-11-28
i have an idea, and before i mess up my entire computer i want to run it by you guys. I want to downgrade to 8.04. i already have a separate /home partition, so could i: 

run: dpkg --get-selections > pack.log
reinstall 8.04
enable backports and other software sources (as i do now)
run: dpkg --set-selections < /backup/installed-software.log [then] select [select i]
update and upgrade a few times
edit fstab and remount my /home partition

my goal is to downgrade to 8.04, but to keep all the programs, all the configurations, and all the themes, and media that i have now. ideally after a few hours of work, my laptop would be exactly like it is now (only better).



also, i would like to partition off 15gb or so, and play with fedora or some other flavor of linux, should i install this first, or does it not matter?

---

### Post by soro2005 on 2008-11-28
This may or may not work to your satisfaction. I'd guess it doesn't. There're a few packages that have been discontinued, and others that didn't ever exist in Hardy. Also, many of the config files have probably changed considerably. So they are backward compatible only to a certain degree.

---

### Post by ByteJuggler on 2008-11-28
If I understand you correctly, you're intending to 
- save your installed package list, then 
- wipe your root partition and 
- do a clean install of 8.04, then
- update it, then 
- finally reinstall the same packages that you had had installed before on your new 8.04 installation, 
- all the while keeping your existing home partition.

I'd say it's worth a try but there's not guarantees of course.  You *should* be able to fix any incompatibilities after the reinstallation/downgrade, I think.

Make sure you have backups of everything you absolutely cannot lose, and ideally a fully system backup (if possible.)  

You can just tell the installer not to format your home partition, and if you use the same username during installation as what is already there, you'll magically log into your existing account after installation with all customizations still in place.  (I do that type of thing with "upgrade" reinstallations on my laptop which also has a seperate home, and it works fine, mostly although I've not yet bothered to try automating the reinstallation of packages like you want to -- been wanting to try it but haven't gotten around to it yet.)

---

