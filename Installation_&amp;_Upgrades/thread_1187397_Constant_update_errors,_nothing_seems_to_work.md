---
title: "Constant update errors, nothing seems to work"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by KWhistle on 2009-06-14
Had an autoupdate a couple weeks ago.  Got some error message about evolution (whatever that is) and since then nothing seems to be installing.

Initially had the following error: Sub-process /usr/bin/dpkg returned an error code (1)

 I searched for a solution here and there, and ended up trying the following commands amongst others:
sudo apt-get -f install
and
sudo dpkg --configure -a

and a bunch of others.  Nothing seems to work.  Here's the output from my terminal:

> alex@alex-laptop:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ekiga evolution-common evolution-documentation-en
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 57.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `libedataserver1.2-11' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

Would really appreciate if anyone can provide a solution.

---

### Post by cariboo on 2009-06-14
Go to System-->Administration-->Synaptic-->Edit-->Fix Broken Packages, to see if that will help fix the problem.

---

### Post by KWhistle on 2009-06-14
Thanks for the advise.  Tried it, it said that it fixed it, but it didn't solve the problem.  I get the dpkg error 2, which seems to be the recurrent theme as of recent.

---

### Post by KWhistle on 2009-06-15
bump

---

### Post by KWhistle on 2009-06-15
After a few days of searching found a working solution.  Not the best solution, but it got my system to work, at least for now.  

As it seems to be a common problem--there are tons of posts about it, but no real solution that I've seen, here's what I've done, based on something I saw somewhere else:

My problem was evolution-common, evolution-documents-en (or something like it), and ekiga.  Dpkg would not remove it, and would not go on with any other updates/installations because those programs were not removing.  

I went to /var/user/dpkg/info and deleted every file that had evolution-common, evolution-documents-en, and ekiga in their names.  Sample input in terminal:

sudo rm -f evolution-common*

After that I ran update and upgrade via app-get (there are plenty of posts on the subject that detail which commands to enter in order to do that.

Dpkg gave me some "serious errors", but it finally skipped over these, instead of getting stuck on them, and actually installed the system upgrades that I selected before synaptic/update manager became disfunctional. 

Hope this helps others.

K

---

