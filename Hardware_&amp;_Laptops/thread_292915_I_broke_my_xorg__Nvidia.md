---
title: "I broke my xorg // Nvidia"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by greenwom on 2006-11-04
I installd the nvidia driver via Automatiz, had twinview all set up and then tried running compiz (problems with twinview).  I removed the compiz packages and nvidia-glx is gone and I can install it.  I get: 

```
 Depends: nvidia-kernel-1.0.9625
```

What to do, there isnt a package in the repos.  I also notices that the quote button on my keyboard doesnt work.  if I dpkg-reconfigure xserver-xorg It doesnt fix it?  

What to do?

thanks

---

### Post by jamesford on 2006-11-04
ur not alone

---

### Post by greenwom on 2006-11-04
Fixed it!
I dont have the specifics.  I updated my sources.list to a complete one from the forums.  removed all nvidia stuff I had installed and then reinstalled nvidia-glx.  I wasnt keeping track.

My keyboard is still messed up a bit, not quotes 

....

---

### Post by useResa on 2006-11-05
I am quite new to Ubuntu and not a specialist, but maybe this may help.
You indicate that the nvidia driver you are using is 9625. The current one in the repos - as far as I understand - is 8776.

Therefor, maybe this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=263851") can help you fix the problem.
Particularly Option 2 about installing Nvidia drivers.

---

