---
title: "How to completely remove and reinstall openoffice.org"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by h4ck3r on 2009-05-07
Hey guys, I was trying to upgrade to 3.1 today, now, I just want to get it back to normal. How do I completely remove all packages of it that I have, I think I got it, but maybe I missed a few, and then install it the way it was installed when I did a clean install from the disk. I have gotten it close, but the theme is still off. Even with the openoffice.org-kde package installed. Any tips?

---

### Post by h4ck3r on 2009-05-07
What I mean by the theme is off, is it doesn't look like the default openoffice. I really just want to get it exactly the way it was before I messed with it :P

Don't you hate the feeling... why did I ever mess with it in the first place?

---

### Post by h4ck3r on 2009-05-07
*bump*

---

### Post by colau on 2009-05-07
To install
aptitude install openoffice.org

To remove 
aptitude remove openoffice.org

Do they work?

---

### Post by h4ck3r on 2009-05-07
Hmmm, I have been using apt-get install / remove (I'm an old ubuntu user) Apparently, they've improved and aptitude does things differently and has special rules over apt-get... that worked wonders. THANKS!

I did an apt-get remove openoffice.org*.*
Then I did an aptitude install openoffice.org

but my theme was still messed up, I then did an aptitude install openoffice.org-kde

*edit* Btw, I removed my ~/.openoffice.org directory too.

And it was all back to normal.

Thanks.

---

### Post by h4ck3r on 2009-05-07
Clearly aptitude handles packages differently than apt-get does, it downgraded some packages and did some cool stuff, I'm impressed with the changes they've made!

---

### Post by sgosnell on 2009-05-07
"sudo apt-get remove" doesn't delete configuration files.  For that, you need to use "sudo apt-get purge".  In Synaptic, you can mark the open office packages as "mark for complete removal" to get the same results.

---

### Post by ranavita on 2011-03-14
> **sgosnell said:**
> "sudo apt-get remove" doesn't delete configuration files.  For that, you need to use "sudo apt-get purge".  In Synaptic, you can mark the open office packages as "mark for complete removal" to get the same results.

very good solution.

---

### Post by Hagar Delest on 2011-03-15
See also: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

