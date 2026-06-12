---
title: "After upgrading it keeps freezing, now won't boot at all, &quot;no init found&quot;"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by peacechicken on 2009-06-28
I have this problem posted elsewhere on the forum but so far I haven't heard anything. What happened to Ubuntu, I used to get really fast support, and now *nothing*. If I wanted that, I'd go back to Windows. Very disappointing. :(

I just upgraded to 9.04 and it seemed to work fine, than it froze up when I was using Firefox, so I hit restart. It wouldn't boot up again, just gave me this:

```
kinit: No resume image, doing normal boot
mount: mounting /dev/disk/by-uuid/{some numbers} on /root failed invalid: argument
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```

After finding another person with this issue I fixed it once by booting the live CD and running "sudo e2fsck /dev/sda1" but it froze up again and now that command doesn't do anything, it doesn't recognize any drives at all.

Hope someone can help, my computer is completely unusable at this point. Wish I never upgraded and stayed with 8.10.

---

### Post by SoftwareExplorer on 2009-08-05
If you start up a liveCD, can you see your files? Second, do you have a way to back them up if you need to reinstall?

---

### Post by peacechicken on 2009-08-06
> **SoftwareExplorer said:**
> If you start up a liveCD, can you see your files? Second, do you have a way to back them up if you need to reinstall?

Sometimes it would show my harddrive thru liveCD, sometimes it wouldn't. I concluded it was probably a failing drive and bought a new one. Since then I haven't had any problems *::knock on wood::*

And yes, everything was backed up, fortunately!

---

### Post by SoftwareExplorer on 2009-08-06
Glad you got it working. Happy Ubuntu-ing!

---

### Post by peacechicken on 2009-08-07
Thanks for asking! After seeing your signature I'm gonna join Ubuntu Counter now, pretty cool. :)

---

### Post by SoftwareExplorer on 2009-08-08
> **peacechicken said:**
> Thanks for asking! After seeing your signature I'm gonna join Ubuntu Counter now, pretty cool. :)

I consider it a way to give hard evidence when software or hardware developers say why should I port this Ubuntu?(and thereby usually all of Linux).

---

