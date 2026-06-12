---
title: "How can you see past websites visited if the history was deleted?"
date: 2008-07-19
forum: General Help
---

### Post by danzi13 on 2008-07-19
I'm new to the forums and ubuntu, so i hope ive done this correctly

Anyway
There is a site i really need, but i dont know the name. I deleted my history earlier without thinking, and now i cant use the site.
So, my question is. 

How can you see past websites visited if the history was deleted? Or can't you? 

Because i know on XP they are kept as something like A TIF file in C:/ drive without you actually knowing

p.s - I wasnt sure what it meant when it asked me for a prefix, so i just put ubuntu.

---

### Post by llebegue on 2008-07-19
I don't thinks there is any solution to this outside some forensic analysis of the disk where the information was previously stored ... bu perhaps someone else knows ...

---

### Post by flytripper on 2008-07-19
on windows it was via an index.dat file but i am yet to learn of any secret system logfile for linux and whether this os is also just as arbitrary

---

### Post by drs305 on 2008-07-19
If you cleared your history but did not clear the 'cookies', you might be able to wade through the entries in cookies.txt to see if the site placed a cookie on your machine.

---

### Post by danzi13 on 2008-07-20
> **drs305 said:**
> If you cleared your history but did not clear the 'cookies', you might be able to wade through the entries in cookies.txt to see if the site placed a cookie on your machine.

Where are the cookies stored? Is there a place on the hard drive?

---

### Post by pauper on 2008-07-20
```
cat $HOME/.mozilla/firefox/*.default/cookies.txt
```

---

### Post by p_quarles on 2008-07-20
Cookies are in Firefox's configuration directory, usually located at:
```
/home/username/.mozilla/firefox/XXXXXX.default
```
You'll see a "cookies.txt" file as well as few files related to the SQLite database Firefox keeps for this purpose.

Other browsers will store cookies differently.

---

### Post by drs305 on 2008-07-20
> **danzi13 said:**
> Where are the cookies stored? Is there a place on the hard drive?

If the file is in a non-standard location or you are using a non-mozilla browser this command will find files named 'cookies' if they are on your main partition:
```
sudo find / -type f -iname cookies*
```

---

