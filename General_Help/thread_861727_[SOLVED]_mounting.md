---
title: "[SOLVED] mounting"
date: 2008-07-16
forum: General Help
---

### Post by pikabuntu on 2008-07-16
How to mount something at login?

---

### Post by chicken101 on 2008-07-16
I suppose you are talking about some sort of external storage device?

What you need to do is to add it to your fstab file, I'll help you out with that- if you are indeed talking about a storage device.

---

### Post by pikabuntu on 2008-07-16
it is a shared folder :)

---

### Post by scragar on 2008-07-16
I don't think you can mount something at login, but you can mount things at boot, this is done by editing the fstab, although I do recomend(infact if I cold see you in person I'd insist on it) that you back it up before attempting to edit it at all, since it's such a key file.
```
gksudo gedit /etc/fstab
```


EDIT:
Not sure about shared files, so disregard my statement, that was for local devices etc.

---

### Post by pikabuntu on 2008-07-16
what would happen if this file is messed up?

---

### Post by chicken101 on 2008-07-16
I believe I found the answer you seek.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20]("http://ubuntuforums.org/showthread.php?t=249889&highlight=umount+nfs&page=20")

Hope that helps you.:)

---

### Post by scragar on 2008-07-16
> **pikabuntu said:**
> what would happen if this file is messed up?

Depends, worst normal problem is that you have to press ctrl+D to continue boot because a non-essential partition info has been messed up(usually things like external HDs or whatever), or if for some reason your root file system is unmounted it doesn't auto-mount back on(which can cause a serious lack of functionality till you remount it or restart), absolute worst case however is that it refuses to boot at all, since you accidentally messed up anything to do with the partition mapped to / (the root file system), which is a pretty major problem for booting(easy enough to fix if you've got a liveCD handy though). As is it's always best to back it up before editing it, just because it's so easy to accidentally delete a letter or 2 without realizing it.
Although none of these are very likely I have seen people make these errors before then not be able to role back the edits.

---

