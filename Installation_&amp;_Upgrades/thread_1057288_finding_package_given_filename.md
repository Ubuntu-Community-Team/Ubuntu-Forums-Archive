---
title: "finding package given filename"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by drhex on 2009-02-01
In synaptic one can, given a package, get a list of installed files.
Is there a way to do that in reverse, i.e. given a filename find out the name of the package?
I tried reading the man-page for apt-cache but didn't find such a search option.

---

### Post by BigBob on 2009-02-01
Hi,

Fist of all install apt-file :

sudo apt-get install apt-file

then update it :

sudo apt-file update

And finally use it :

bigbob@bigbob-laptop:~$ apt-file search /usr/bin/ldd
libc6: /usr/bin/ldd
bigbob@bigbob-laptop:~$

Here you can see the file "/usr/bin/ldd" come from the libc6 package ...

A++

---

### Post by Partyboi2 on 2009-02-01
You can also do a search [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/")

---

### Post by drhex on 2009-02-01
Thx for the quick reply!

"apt-file update" keeps saying:

Can't get [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/intrepid/Contents-i386.gz](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/intrepid/Contents-i386.gz)

I'll try again later and see if some server was just temporarily offline.

---

### Post by drhex on 2009-02-01
Thanks Partyboi2, that website did the job!

---

### Post by drhex on 2009-02-01
Hmm. Tried to mark the thread as [SOLVED] as per the suggestion in Partyboi2's sig, but there is no such option in the "Thread tools" menu! (And an "edit" on the first post won't let me edit the subject)

---

### Post by Partyboi2 on 2009-02-01
> **drhex said:**
> Hmm. Tried to mark the thread as [SOLVED] as per the suggestion in Partyboi2's sig, but there is no such option in the "Thread tools" menu! (And an "edit" on the first post won't let me edit the subject)
The option to mark threads solved has been temporally disabled due to forum database problems. 

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

