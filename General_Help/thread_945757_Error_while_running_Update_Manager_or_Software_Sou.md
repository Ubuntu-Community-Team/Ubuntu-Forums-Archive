---
title: "Error while running Update Manager or Software Source"
date: 2008-10-12
forum: General Help
---

### Post by blueshift9 on 2008-10-12
When either trying to run the Update Manager or Software Sources, this error pops up:

> 'E:Problem parsing dependency Depends, E:Error occurred while processing btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I have looked and tried to disable some of the software sources that have been added since installation, but the problem still pops up. Thanks!

---

### Post by ashish.nopc0de on 2008-10-12
I don't Know, if there was some problem with ubuntu repositeries.
Even i had the same problem 10 mins ago ,which is now solved.
some of the lines in sources.list were changed from "hardy" to "harty" 
during apt-get update.
check your sources.list file, it might have some similar errors.

---

### Post by ben2talk on 2008-10-13
Bump

E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages)


tried apt-get -f install
tried apt-get clean
tried apt-get update:
[LIST=1][*]Fetched 5B in 17s (0B/s)  Reading package lists... Error! W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_hardy_partner_binary-i386_Packages) E: Problem parsing dependency Depends E: Error occurred while processing btnx (NewVersion1) E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages E: The package lists or status file could not be parsed or opened.

[/LIST]

I hope you guys have some ideas! I had a few updates yesterday, and it seemed fine - but then I wanted to do a reboot and did a 'save session' which took a while to recover from! (meaning that after finishing the session, closed everything and saved 'empty' session and rebooted and it wasn't clean - took 4 reboots to get a clean start).


OK guys, I got around this (easy GUI fix)

System>Admin>Software sources (enter password)

or command line: 
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

I had two entries starting with epoubuntusoftware - so I removed them. Check it now (ALT+F2 type 'gksu synaptic')
Hopefully synaptic will load up properly.

Now I just need to remember why I had 'repoubuntusoftware' enabled - back to google!

---

### Post by caro0067 on 2008-10-13
Thank you! This fix worked for me.

---

### Post by blueshift9 on 2008-10-14
Ashish (the 2nd post) was correct as some of the repos were changed to "harty" instead.....I can't believe I didn't noticed, just opened them up and edited to "hardy" and it was all good to go.

---

