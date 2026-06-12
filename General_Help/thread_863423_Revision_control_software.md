---
title: "Revision control software"
date: 2008-07-18
forum: General Help
---

### Post by WrathofthePenguin on 2008-07-18
I need to backup a file each time it's opened. The user is not accustomed to backing up the file regularly, so in several instances data has been lost when there's been a problem. So, I'm thinking that if it's backed up every time it's opened, then the data loss is limited.

I was thinking that if it's copied to a new sequentially numbered file each time (file5 is copied to file6 when it's opened) that would give me a running set of revisions. However, I would assume that there is a better way to do what I need.

I found a lot of revision control software on wikipedia, but I'm not familiar with any of it. Ideally, the software would work in both windows and Ubuntu.

If anybody has experience with software like this I'd love to hear your comments. I don't need a very complex setup - it's a pretty simple situation in this case.

---

### Post by diaa on 2008-07-18
Although you didn't give enough details that helps pick the most suitable VCS, I generally recommend Subversion, especially that it has very mature set of GUI tools and there are [several Subversion guides at lifehacker]("http://lifehacker.com/tag/subversion/"), aimed at users as opposed to software developers.

---

### Post by WrathofthePenguin on 2008-07-18
Thanks for the tip - I'm testing it out now (the Lifehacker articles are nice).

---

### Post by txcrackers on 2008-07-19
The problem with using an RCS is the same one you're running into with the user not doing backups: the user is going to have to do something to check in their changes.

I'd recommend looking into automated backup solutions, either distributed or stand-alone. There are plenty that are cross-platform, either F/OSS or proprietary. That way you don't have to rely on the user remembering to do something.

---

