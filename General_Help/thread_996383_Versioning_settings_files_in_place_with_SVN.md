---
title: "Versioning settings files in place with SVN"
date: 2008-11-28
forum: General Help
---

### Post by grundunkus on 2008-11-28
On a server I used to have to do some admin work on a few years ago we used to use RCS in each of the directories we wanted to keep a history of changes to certain files in... just simple co and ci commands.

I'd like to do this kind of in-place versioning with Subversion and spread a bit further afield than the /etc directory... for eg things like /home/username/.gconf and such.

Has anybody had any experience doing this, and if so, how did you make it work? The best way I thought of was making the root filesystem an .svn working copy but with lots of things in the ignore list, but that would lead to some pretty freaking unwieldy ignore lists in places! Are there also issues with permissions that this would raise, and if so, how would I get around those?

---

