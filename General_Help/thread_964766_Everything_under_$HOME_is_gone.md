---
title: "Everything under $HOME is gone"
date: 2008-10-31
forum: General Help
---

### Post by magnus.gylfason on 2008-10-31
After last nights updates (still on 8.04) when I tried to log into today I was greeted with the message:

"your $HOME/.dmrc file has incorrect permissions problem"

I logged in using safe terminal and for some reason my homefolder was owned by root. So I did a chown user:user /home/user and logged back in.

And saw that every single pice of data in my home folder was gone. All of it.

HELP

---

### Post by magnus.gylfason on 2008-10-31
Ive found my data. I have my home folder on a seperate partition and for some reason ubuntu fails to mount it (but doesnt complain) after the updates.

And whats with those weird UUIDS in fstab?

---

### Post by roeland on 2008-10-31
UUIDs are globally unique IDs for your disk volumes. Should you ever move a disk to another controller in your PC, the thing will suddenly become (for example) /dev/sdb instead of /dev/sda, but the mounter will still recognise it by its UUID and mount it at the same point as before.

That might have prevented your 'lost' volume problem, but I don't know what your fstab looked like. I find it strange that a 'normal' update would have changed your fstab, though.

---

