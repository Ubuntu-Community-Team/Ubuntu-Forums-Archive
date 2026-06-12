---
title: "Grub error 17 help"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by jackjaunty on 2009-06-16
Hi everybody,

I am having boot up problems with my dell studio, which was a dual boot with vista and Ubuntu 9.04 . Few days back i was trying to install OS X to make it a multi boot system. But when I tried to create new HFS partition, i screwed up my system and i guess the MBR was corrupted and now I am not able to boot!! :( 

I get the grub error 17. I suppose the reason for this is the change in the drive name, earlier "/dev/sda6" had the linux, now its "/dev/sda7". Could this be a reason ? 

I also thought of re installing grub with a live Ubuntu CD, but could not proceed further at all, since 
grub> root "<tab>"
does not have any valid inputs. I get " Error1: Filename must be either an absolute pathname or blocklist"

Thanks a lot!

---

### Post by merlinus on 2009-06-16
You might try supergrub.  Otherwise, look at what this gives:

```

sudo fdisk -l

```

and you might be able to reinstall grub.

---

### Post by swisstone198 on 2009-06-16
Edit

---

