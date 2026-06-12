---
title: "Questions about setting up server edition"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by minkey32 on 2009-03-19
I have delved into the world of Linux a little but my only experience is with redhat.  I've heard a lot of good things about ubuntu and I just have a few questions about set up.  

I have a 64-bit system with a couple spare harddrives, I'm planning on setting up a home file server that eventually will be accessible from the outside.  

I would like it to see all the hard drives as one (if possible).  Can I do that during the install or is that something I set up after?  I understand RAID but I'm a little confused about what LVM is.  Which one would be better with what I'm planning on doing?  I'm not worried about backup because I have an external harddrive I keep all my important stuff on.    

it should be accessible by my windows network.  I know to make sure samba is installed but what other services would you suggest I also include so I can set up the outside access later?  

any other tips or suggestions would be greatly appreciated.  Even if it's a "Check google for this, jackass".  

Thanks!

---

### Post by cariboo on 2009-03-19
THe only thing that raid does for you, is that if one of the drives in the array goes defective, your data is not lost. Using LVM makes it appear that instead of several hard drives, you have one large drive. For more info on LVM have a look [here]("http:///en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)").

Jim

---

