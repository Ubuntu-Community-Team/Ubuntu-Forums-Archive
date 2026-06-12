---
title: "Work offline in firefox?"
date: 2008-08-15
forum: General Help
---

### Post by Mashy on 2008-08-15
Whenever I start firefox it is always set into 'work offline' mode, and I have to click on file, then uncheck work offline so it will actually connect to the internet. 

Is there any way to make it so that it is always in work online mode, so I can browse as soon as I load it up?

Thanks.

---

### Post by PGScooter on 2008-08-15
Hi Mashy,

Yeah, that's annoying isn't it!

Don't despair, this thread should solve your problem, it did mine.
[http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)

Post back whether that works or not for you. I hope it does.

---

### Post by Tom--d on 2008-08-15
> **Mashy said:**
> Whenever I start firefox it is always set into 'work offline' mode, and I have to click on file, then uncheck work offline so it will actually connect to the internet. 

Is there any way to make it so that it is always in work online mode, so I can browse as soon as I load it up?

Thanks.

Yes!
If you are not using Network Manager. Remove it. That's causing the offline mode.
```
sudo apt-get purge network-manager network-manager-gnome
```

---

### Post by pbhj on 2008-08-19
[COLOR="RoyalBlue"][http://ubuntuforums.org/showpost.php?p=5060822&postcount=6](http://ubuntuforums.org/showpost.php?p=5060822&postcount=6)[/COLOR] works for me whereas fixes involving pref.js and about:config did not.

---

### Post by brunolabs on 2008-08-19
> **Tom--d said:**
> Yes!
If you are not using Network Manager. Remove it. That's causing the offline mode.


Everything else keeps working after removing NM? If so, what does NM do?

Thanks.

---

### Post by brunolabs on 2008-08-21
bump

---

