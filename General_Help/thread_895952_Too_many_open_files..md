---
title: "Too many open files."
date: 2008-08-20
forum: General Help
---

### Post by pwnzor on 2008-08-20
Hello, i am proud ubuntu 7.10 user on my webserver. 
I use uTorrent (1.8) + wine (latest) and in 8-10 active torrents i got "Error: Too many open files". 
How to change this? 
- I tried ulimit -n (back to 1024 after reboot)
- I tried edit etc/security/limits.conf
- I tried something with fs.file.max=

Any other ideas? I dont have more. Thanks in advance for help.

---

### Post by fedex1993 on 2008-08-20
I would actually try using rtorrent. You can have an unlimited amount of torrents open. I love using it alot.

---

### Post by mb_webguy on 2008-08-20
Or Deluge, particularly the newest version from the Deluge website.

---

### Post by pwnzor on 2008-08-20
I provide uTorrent to my friends, they use WebUi, its pretty easy to split users. Every user have other url for uT etc. I really want fix it but dont have more ideas, ulimit -n always shows 1024 :(

How to run 3-4 deluge's on same user? (i am newbie).
I get error message: "Dependency is not satisfable: libboost-date-time1.34.1 - What it is?

---

### Post by mb_webguy on 2008-08-20
*blink blink*  Um... good question.  Deluge does have a web interface, but I've never used it.  I'm not sure whether it allows multiple users or not.  Maybe [this link]("http://phorolinux.com/how-to-use-deluge-web-user-interface.html") will help...

---

### Post by fedex1993 on 2008-08-20
> **mb_webguy said:**
> *blink blink*  Um... good question.  Deluge does have a web interface, but I've never used it.  I'm not sure whether it allows multiple users or not.  Maybe [this link]("http://phorolinux.com/how-to-use-deluge-web-user-interface.html") will help...

yes deluge is good to use with there web ui

---

### Post by pwnzor on 2008-08-21
Deluge looks nice, have webui etc but theres one problem: Many private trackers doesnt support it, i try move 2 friends who dont use so much elite trackers, and 2 stay on ut.

Thanks for help.

---

### Post by mb_webguy on 2008-08-21
Just because a private tracker doesn't support it (and by that I assume you're talking about detecting and recording upload and download activity), it doesn't necessarily mean you can't use Deluge.

For example, I use Demonoid, which monitors your total upload and download amounts and is technically supposed to drop your membership if the ratio gets too low.  However, Demonoid recognizes that some of the clients used by its members don't accurately report those statistics, and therefore don't actually pay much attention to the ratio.

---

### Post by pwnzor on 2008-08-21
Now i think about rtorrent but i dont know how to run separate 3-4 rtorrents for 3-4 persons. I am newbie, i googled some etc but i cant find good solution/explaination

---

