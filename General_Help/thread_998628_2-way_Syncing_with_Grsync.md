---
title: "2-way Syncing with Grsync?"
date: 2008-12-01
forum: General Help
---

### Post by Chaconne on 2008-12-01
Hello, all,

I have a question about Grsync: How can I synchronize files in 2 folders in both directions depending on the most updated files in either folder? I setup a profile in Grsync and give it a try but found out it always copy different files from source to destination, even if the files in source folder is older.

I can do the job in Unison, but the catch of Unison is it can only be done successfully in a partition mounted by current user. That means I can not sync folders on partitions mounted on startup with /etc/fstab(root owned). I've set PERM=0 but it doesn't help.

I started using Ubuntu not long ago so I'm kinda noob. Under Windows, I can do the job with SyncBack Personal Edition with great convenience. All I want is a program that is able to perform the same task under Linux.

Thanks in advance.

---

### Post by Chaconne on 2008-12-02
bump.

---

### Post by edzell on 2010-11-27
Please, what is "bump" supposed to convey?

---

### Post by HereInOz on 2010-11-27
I can't help with the GRSync question, but a "Bump" is simply a technique to get your post back to the top of the list, if it has gone unanswered for a couple of days.

In this case, the "Bump" was unsuccessful, as no-one has yet answered the question, and I can't help with it.

---

### Post by Wobblybob on 2010-11-27
Hi, have a look at Unison I think it does what you want

[[COLOR="Navy"]https://help.ubuntu.com/community/Unison[/COLOR]]("https://help.ubuntu.com/community/Unison")

---

### Post by edzell on 2010-11-27
> **HereInOz said:**
> I can't help with the GRSync question, but a "Bump" is simply a technique to get your post back to the top of the list, if it has gone unanswered for a couple of days.

In this case, the "Bump" was unsuccessful, as no-one has yet answered the question, and I can't help with it.
OK thanks. It's an old thread but I was interested in any answers. So far as I can discover rsync & grsync do only one-way synchronising. For 2-way, unison seems like the best bet though I haven't tried it yet.

Guess I'll mark this solved - edit - maybe I can't 'cause it's not my thread.

Edit 'smore: Meld provides a nice, somewhat manual way to sync 2 folders; opens them side by side, highlights differences and lets you copy missing or changed files to right or left, or delete them; even lets you open some types of file to examine them before you decide.

Definitely LAST edit: Don't think Meld works across network; only on local machine.

---

