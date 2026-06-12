---
title: "Can Ubuntu handle external drives?"
date: 2010-04-29
forum: Hardware
---

### Post by jallgoth on 2010-04-29
Hi

according to [https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713), Ubuntu (kernel?) cant handle some external drives. **Does this still apply? How can one determine if one is affected?**

Background:
Half a year ago I deployed an Atom-machine to act as a home-server, doing torrents, NAS and a few other things. I migrated all my data from over the years to a 1.5 TB Western Digital drive, formatted HFS+ with journal off. This to be able to plug it into a computer running OS X.

I unmounted it a few times, to use it in OS X, i used 'umount' as I am accustomed to. By now the mac has complained several times about file system corruption and I have resolved them with fsck.hfsplus and a OS X app called Diskwarrior. 

But, a week ago I noticed that several directories were mysteriously empty. It turns out that **large parts of my data are corrupted.**

Is this normal nowadays? The 4 year old launchpad-bug seems to go unnoticed....

---

### Post by 3177 on 2010-04-29
I own a 1.5TB external iomega
it has no problems working with ubuntu
but thats only one brand...

---

### Post by 3177 on 2011-01-26
well, if ur still listening.....
Western digital hard disks seem to have no problem with Ubuntu.
If something was coming up as corrupt, well its corrupt.
its been almost a year and I have no problems with either the Iomega or Western Digital HD's. No corruptions, no problems.

---

