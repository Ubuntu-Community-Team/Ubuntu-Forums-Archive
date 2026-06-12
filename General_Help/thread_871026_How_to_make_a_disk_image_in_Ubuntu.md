---
title: "How to make a disk image in Ubuntu?"
date: 2008-07-26
forum: General Help
---

### Post by softtower on 2008-07-26
I have a perfectly working Ubuntu system installed on my ThinkPad. I do backups with rsync and everything is great.

However, I don't back up everything, and in case of a hard drive failure I'll have to reinstall/reconfigure a lot of stuff, because I only backup my data and /etc directory.

What I want to do is to make an image of my entire hard drive. I know about partimage, but it deals with partitions only, and it's a pain in the butt to restore multiple partitions and I could never restore MBR properly with it.

So... is there something in Linux world that takes a snapshot of the entire drive, that I can "apply" to a bare metal new drive?

---

### Post by softtower on 2008-07-26
Thanks to IRC, the problem is solved: 
```
man dd
```

---

