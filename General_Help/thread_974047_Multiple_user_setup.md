---
title: "Multiple user setup"
date: 2008-11-07
forum: General Help
---

### Post by EpidemikE on 2008-11-07
Hey, I wanted to create  a desktop for my Brother and his 3 kids to use and instead of XP, I am going to install Ubuntu.

My question is, are there any guides, tips or tricks for multiple user accounts in Ubuntu?

Any suggestions would be greatly appreciated.

---

### Post by geirha on 2008-11-07
It's fairly easy. During installation you create the first user with administrative rights, which would typically be your brother's user. When it's installed, log in with that user and go to System -> Administration -> Users and Groups, click the Unlock button and type in the password to be able to do administrative tasks. Then you can add users for the kids. If the kids should be allowed to do administrative tasks (install programs, create new users, run programs as root with sudo/gksu etc) set their profile to Administrative user, if not, set profile Desktop user.

Do note that kids will eventually figure out how to surpass this. They can just boot the liveCD, mount the filesystem and give themselves admin priviledges.

---

### Post by EpidemikE on 2008-11-07
Thats what I've done already so I am glad to hear that I did things right.

I kind of like the way Ubuntu manages the users > XP. Only thing is i wish there was a way to replicate a "golden copy" profile so as I wouldn't have to replicate the desktop conditions on all 3 user IDs.

This will be their first foray into Ubuntu and I haven't told them yet. I know I am going to get lots of questions asking me how things work but it shouldn't be so bad. It'll be better for them in the long run.

---

