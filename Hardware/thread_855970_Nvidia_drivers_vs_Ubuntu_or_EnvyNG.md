---
title: "Nvidia drivers vs Ubuntu or EnvyNG"
date: 2008-07-11
forum: Hardware
---

### Post by showgun22 on 2008-07-11
8.04 I just replace my ATI card on my PC for a Nvidia I could not get the Ubuntu drivers to work with special effect and even worst with the EnvyNG. At the end I installed the drivers from NVIDIA website and it worked like a charm.

I just would like to know if the drivers from Nvidia are better in some way or more complete?
Thanks

---

### Post by sdennie on 2008-07-11
This is a hard question to answer.  Because the nvidia drivers are closed source, they can't be well integrated into Ubuntu.  The drivers from the nvidia website are obviously the most up to date but, they are also hard to install, maintain, etc.  

For most users, I recommend using the Ubuntu drivers, then, if they don't work, envy, then if it doesn't work, the drivers from the website.  Even if you have successfully installed the nvidia drivers from the website, you are going to have problems:

1) Depending on how you've installed they may not work when you reboot.  To fix this, try: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2)

2) The drivers will break every time you install a major kernel update.  To fix this, try: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

3) When xserver-org-core updates, compiz will no longer work.  To fix this, you have to completely re-install the drivers.

So, the nvidia drivers from the website are likely to work with a wider range of hardware but, they are very problematic.

---

### Post by showgun22 on 2008-07-11
THanks for the info I will save those links
so far it has been working flawlessly for a week so hopefully it will keep untill next big upgrade..
when time comes I will have to retry Ubuntu or EnvyNG.. Untill then I'll keep my finger cross..
Again Thank you...

---

