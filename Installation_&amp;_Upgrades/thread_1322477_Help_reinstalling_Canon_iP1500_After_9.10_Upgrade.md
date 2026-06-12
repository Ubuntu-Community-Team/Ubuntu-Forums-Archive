---
title: "Help reinstalling Canon iP1500 After 9.10 Upgrade"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by ngrieb on 2009-11-11
So, I upgraded to 9.10, and now the hacked Canon drivers that I was using with bjfilter and libcnbj2.5 no longer will work because bjfilter seems to have a dependency on libcupsys2, which seems to now be outdated...

Anyone else have this problem too?

---

### Post by Menthu_Rae on 2009-11-11
Hey mate,

**Use the same process** in my thread here:

[http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363)

Or this thread here:

[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)

Should get it working ;) If you get stuck, be sure to post back here.

---

### Post by ngrieb on 2009-11-12
Um...ya the thread is talking about the iP1900, which seems to have downloadable dev drivers. My printer is the iP1500, which as far as I checked last was not very well supported, and had to be hacked together by someone, that then posted it to lib here: 

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

I don't know how get the files for modification...maybe you can help me with that, and then we can see if they are fixable.

Thanks

---

### Post by Menthu_Rae on 2009-11-13
> **ngrieb said:**
> Um...ya the thread is talking about the iP1900, which seems to have downloadable dev drivers. My printer is the iP1500, which as far as I checked last was not very well supported, and had to be hacked together by someone, that then posted it to lib here: 

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

I don't know how get the files for modification...maybe you can help me with that, and then we can see if they are fixable.

Thanks

Hrmmm, you would need to download the .deb's from there somehow and then modify them in regards to the dependency support as per the other threads.

I'm not sure how to do this as attempting to access the repo:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/)

Gives me a 403 Forbidden. You may want to email the owner of the site/repo and get the debs from him or get him to fix them up.

Otherwise if someone has the debs cached on their system - they could possibly upload them here? ;)

I'm not sure what the legalities are surrounding this... so I think the best route is to email the creator of the debs/provider of the repo. :o

---

