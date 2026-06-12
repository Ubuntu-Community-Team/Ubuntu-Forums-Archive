---
title: "compiz fails"
date: 2008-11-17
forum: General Help
---

### Post by Sponzenbroekske on 2008-11-17
8.10

My pc starts with compiz on.
Since today my compiz just keeps on failing.
After it quits i restart it
```
yannick@asus:~$ compiz --replace
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
5seconds later it quits AGAIN
```
/usr/bin/compiz: line 775: 23603 Segmentation fault      $*
Window manager warning: Workarounds for broken applications disabled. Some applications may not behave properly.
Window manager warning: Failed to read saved session file /home/yannick/.config/metacity/sessions/1018677b42135faba1122696959672638000000059890018.ms: Failed to open file '/home/yannick/.config/metacity/sessions/1018677b42135faba1122696959672638000000059890018.ms': No such file or directory
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x36000d3 (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


```

---

### Post by hictio on 2008-11-17
You have the Desktop Effects enabled, right? Does Ubuntu give any error when you enable those?
Also, check [this thread](http://ubuntuforums.org/showpost.php?p=6043424&postcount=1).

---

### Post by Sponzenbroekske on 2008-11-17
> **hictio said:**
> You have the Desktop Effects enabled, right? Does Ubuntu give any error when you enable those?
Also, check [this thread](http://ubuntuforums.org/showpost.php?p=6043424&postcount=1).

thx for the input, but the link you gave is also my thread :)

I got desktop effects enabled.

When i start compiz (compiz --replace) then compiz really works, but only for like 5secs and than it stops and i fall back on metacity.

I got no dir metacity :s

---

### Post by sowelie on 2008-11-17
What hardware are you on?  Are you using compiz out of the repos or did you build a later version?  Getting debug info about the seg fault will give you the best direction.  I honestly don't remember how to do that, but googling "debug segmentation fault" seemed to find a bunch of stuff.

---

### Post by hictio on 2008-11-17
> **Sponzenbroekske said:**
> thx for the input, but the link you gave is also my thread :)


Yeah, right, but on the end of the thread you [posted](http://ubuntuforums.org/showpost.php?p=6071818&postcount=20) that it works!
Or, was that on 8.04, and now on 8.10 the thing just explodes once again? Is that so?

---

### Post by Sponzenbroekske on 2008-11-17
> **hictio said:**
> Yeah, right, but on the end of the thread you [posted](http://ubuntuforums.org/showpost.php?p=6071818&postcount=20) that it works!
Or, was that on 8.04, and now on 8.10 the thing just explodes once again? Is that so?

nono it was also the same 8.10 but then it didn't work at all, then i indeed could not get the desktop effects to be work.

Now they are enabled en they stay enabled but compiz just stops working.

So this is another problem.

---

### Post by Sponzenbroekske on 2008-11-19
> **sowelie said:**
> What hardware are you on?  Are you using compiz out of the repos or did you build a later version?  Getting debug info about the seg fault will give you the best direction.  I honestly don't remember how to do that, but googling "debug segmentation fault" seemed to find a bunch of stuff.

ATI RADEON HD2400 mobility (check signature)
I looked at google for the seg fault, but I don't have a clue how to do that :s
And I'm using compiz out of the repos.

---

