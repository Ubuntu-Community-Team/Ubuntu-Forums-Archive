---
title: "Signing key error"
date: 2005-11-17
forum: General Help
---

### Post by cavaughan on 2005-11-17
After reading the post at:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
posted by aysiu concerning my question below, I am still getting the following message when trying to update

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


So, I edited my sources.list to match that of Aysiu's (they were basically the same anyhow), then I did an apt-get update, but I still get a signing key error. Why?

---

### Post by matthew on 2005-11-17
I can't answer the "why" part, sorry. I was able to solve the problem, though.

First, edit your /etc/apt/sources.list by putting a # in front of ***all ***the sources.

Then ```
sudo apt-get update
``` Since there aren't any sources listed what this will do is clear the cache of source info on your computer.

Then go back and remove all the #'s you put in the sources.list file and
```
sudo apt-get update
```and you sould connect without a problem this time.

It's kind of a hack, but it worked for me.

---

### Post by aysiu on 2005-11-17
I haven't experienced that problem, but if it is something someone else has noticed and can replicate, it's probably worth filing a [bug report](https://bugzilla.ubuntu.com/) on.

---

### Post by cavaughan on 2005-11-17
Yeh, look at Matthew just above. His fix worked.

---

