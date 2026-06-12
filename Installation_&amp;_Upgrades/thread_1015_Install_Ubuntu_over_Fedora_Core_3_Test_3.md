---
title: "Install Ubuntu over Fedora Core 3 Test 3"
date: 2004-10-17
forum: Installation &amp; Upgrades
---

### Post by stodge on 2004-10-17
I already have Fedora Core 3 Test 3 installed on two partitions, one / and the other /home. The /home partition is formatted as ext3, which I know Ubuntu supports.

Would it be possible to safely re-format / and install Ubuntu on it without reformatting the /home drive? I just want to keep my emails and bookmarks.

Has anyone tried this yet?

Thanks

---

### Post by FLeiXiuS on 2004-10-17
You should be alright ... just manualy partition ubuntu when you get to the partition screen.  Just format the / partition while having the current /home mount to /home during install.

Also be sure to fix the permissions when finished.

---

### Post by luiska on 2004-10-18
Hi

I installed Ubuntu over FC2 and just had an irritated problem with the partitioning table. Happens when you dont plan this moves carefully.

Luiska

---

### Post by lmn on 2004-10-21
luiska,

What problem did you have with your partition-table?
I was about to make the switch from FC3test2, and when i tried to set the installer to keep and mount my old /home partition the installer told me the partition had some error (not stating what type of error) and told me that i could continue but my /home-partition would not be useable. I stopped there and installed FC3test3 instead.
Is this the same thing you experienced? Did you solve it? How?

//lmn

---

### Post by HungSquirrel on 2004-10-21
> Install Ubuntu over Fedora Core 3 Test 3
Good.  8)

---

### Post by liddish on 2007-09-23
I was wondering if it is possible to wipe fedora with changing the sources.list to the ubuntu repos and then make a apt-get dist-upgrade?
apt-get is installed on that computer I plan to do that.

---

