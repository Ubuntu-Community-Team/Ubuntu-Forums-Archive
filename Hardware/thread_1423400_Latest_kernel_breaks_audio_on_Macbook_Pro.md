---
title: "Latest kernel breaks audio on Macbook Pro"
date: 2010-03-06
forum: Hardware
---

### Post by boarderx1313 on 2010-03-06
I'm using a Macbook Pro 5.5 with 32-bit Karmic. My audio works perfectly using kernel 2.6.31-19 but does not work with 2.6.31-20. Furthermore, in 2.6.31-20, no buttons or sliders show up in gnome-alsamixer. Any thoughts?

---

### Post by anionline on 2010-03-06
I have the same problem on Macbook Pro 5.3!

tks for advice

---

### Post by lypps on 2010-03-06
Me too. Except now I can not get audio or see alsamixer controls in 2.6.31-19 or 2.6.31-14. The kernel update seems to have broken the audio on my MBP 5,3.
I would also very much appreciate any help, advice, and/or fixes that anyone may have to offer.

Thank you,
lypps

---

### Post by skitter.rusty on 2010-03-07
I don't really know much about this problem but I did find this:
[http://ubuntuforums.org/showpost.php?p=4518859&postcount=7](http://ubuntuforums.org/showpost.php?p=4518859&postcount=7)

---

### Post by qhartman on 2010-03-08
I'm seeing this same problem. The alsa backports aren't working, and neither is a manual alsa snapshot install. Anyone found  a bug report on this yet?

---

### Post by anionline on 2010-03-11
Ok, guys, see this

[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Sound)

---

### Post by qhartman on 2010-03-11
Cool. The wiki mentions "a bug", but doesn't point to a bug report. I looked around in launchpad, but it seems my search-foo is failing. Do you know if a report has been filed? Working around the problem is great and all, but unless someone in a position to fix it knows about it...

If I don't find a report soon, I'll post a new one.

---

### Post by lypps on 2010-03-16
Thanks [anionline]("http://ubuntuforums.org/member.php?u=147891")! Running -19 until fix is posted.

---

### Post by djsutton on 2010-03-16
I'm having the same problem on a MacBookPro 5,5 , and I found this.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/535361]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/535361")

I'm not sure if this is the bug to which the MacBookPro community documentation is referring.  It appears to be the same issue, although I haven't had the chance to run the diagnostics they mention to see if it is actually the same thing I'm experiencing.

---

### Post by anionline on 2010-03-28
[lypps]("http://newyork.ubuntuforums.org/member.php?u=1031107")
you welcome!
the bug still exist, i hope is corrected soon, kernel 2.6.31-20 apparently runs better cooler control.

---

