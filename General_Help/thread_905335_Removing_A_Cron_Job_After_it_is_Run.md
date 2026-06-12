---
title: "Removing A Cron Job After it is Run?"
date: 2008-08-30
forum: General Help
---

### Post by david64 on 2008-08-30
Hi. I am always missing auctions I almost always have to snipe them in the dying seconds. So I have made a script in PHP to download my auction list and I would like to run some alarm like running an MP3 player. However, I am not sure how if at all possible it is to delete a cron job after it has been run once.

Does anyone know if this is possible?

---

### Post by augustchau on 2008-08-30
> **david64 said:**
> Hi. I am always missing auctions I almost always have to snipe them in the dying seconds. So I have made a script in PHP to download my auction list and I would like to run some alarm like running an MP3 player. However, I am not sure how if at all possible it is to delete a cron job after it has been run once.

Does anyone know if this is possible?

Well, I don't know if you could find a way of deleting a cron job after it has been executed, but have you tried at command?

Look for the man page of at or this debian website:
[http://manpages.debian.net/cgi-bin/man.cgi?query=at&apropos=0&sektion=0&manpath=Debian+Sid&format=html&locale=en](http://manpages.debian.net/cgi-bin/man.cgi?query=at&apropos=0&sektion=0&manpath=Debian+Sid&format=html&locale=en)

cheers

---

