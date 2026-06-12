---
title: "Directories/files being deleted randomly"
date: 2008-09-11
forum: General Help
---

### Post by virtuallinux on 2008-09-11
I'm running Ubuntu 7.10 on my home server, an old Dell Poweredge, and I've recently had problems with files randomly disappearing.  First is was a file here or there, and now I've had an entire directory disappear.  Fortunately, I'm running nightly backups, so I haven't lost any data yet. I have no idea what might be causing this; I suppose it's possible that I'm unknowingly doing something that's causing it.  I was just wondering if anyone has seen this problem before, and what you might suggest to troubleshoot/fix the problem.

Thanks.

---

### Post by don_xvi on 2008-09-15
Here's a bump, I just discovered that a directory disappeared from my 8.04 RAID with an ext3 filesystem.
I'm not sure how long it's been missing could be a couple of months, I'm quite certain that I (the only user) didn't delete it !  It wasn't in the trash.

---

### Post by JCapriotti on 2008-09-19
Another bump...  i just lost a folder.

I'm 90% sure I did not accidentally delete this folder. And if I did, I'd expect to see it in the trash.

The only weird thing is I have it shared and was changing my shared folder settings to increase security. However, the issue seems to be with the physical directory rather than the share.

---

### Post by virtuallinux on 2008-09-19
Well, I haven't had any problems since my first post, but it seems that this isn't an unheard of problem. I'm running Samba and this is an ext3 filesystem, for the record.

---

### Post by stickmangumby on 2008-09-19
virtuallinux,

Have you tried rebooting your server and doing a filesystem check?

Is it possible that this is caused by some physical problem, like bad sectors on your hard drive?

It doesn't sound like this should be happening at all!

---

### Post by virtuallinux on 2008-09-19
Well, it's possible it's due to some bad sectors.  I've had trouble with this particular hard disk before, and it's been recently formatted. I don't like it, but I'm afraid the disk may be the problem.

---

### Post by stickmangumby on 2008-09-20
If you want to check for bad sectors, and you can afford to not have access to your server for a few hours, I really recommend running a check using SeaTools. It's a bootable CD made by Seagate that will check your harddrives pretty thoroughly for bad sectors and let you know how healthy they are. Run the extended test a few times if you have time.

---

### Post by virtuallinux on 2008-09-21
Thanks for the suggestion; I'll try and do that in the next week or so.

---

### Post by Wisp558 on 2008-09-21
Mmm... Seatools is probably the best HDD checker out there.

---

### Post by deepclutch on 2008-09-21
check for some nasty script(s) in your  / directory or /home/user dir?

---

