---
title: "Samba - Current Shares List"
date: 2008-09-12
forum: General Help
---

### Post by adyroman on 2008-09-12
I've searched the forums and the Ubuntu documentation for quite a while without finding anything significant on the following issue.

Assume somebody creates a Samba share using Nautilus (right click Sharing option on a folder in Nautilus). Then that somebody forgets what was the folder they shared; so they cannot "unshare it". Is there a file or an application that shows what filesystem directories are shared and under what names? I looked in /etc/samba/smb.conf, but that doesn't show shares created with Nautilus. I've also searched all ASCII files in /etc and /var for a specific share name and couldn't find anything. Any idea how to go about this?

---

### Post by ajmorris on 2008-09-12
hi there,
try running ```
smbclient -L <ip or hostname>
```
so if it is your own box, just run smbclient -L 127.0.0.1

AJ

---

### Post by adyroman on 2008-09-12
Yes, that will show the list of shares on my machine; however, if I have a share called "shared_dir" I still have no idea where it is on the filesystem if the share name is not the same with the shared directory name.

To be more specific, if I have a directory like /path/to/a/random/directory/name and I share it as "shared_dir", I can see that I have it shared as "shared_dir" but if I don't know what's the path to it on the filesystem (i.e. /path/to/a/random/directory/name) there is no way I can "unshare it".

---

### Post by adyroman on 2008-09-13
Anybody else?...

---

### Post by javaJake on 2008-09-13
Hit [FONT="Courier New"]Alt+F2[/FONT] on your keyboard, and type in "shares-admin" without the quotes, and hit the [FONT="Courier New"]ENTER[/FONT] key. You'll find a list of shared folders there.

**Edit:** Forgot to mention that the share name is in the Properties window (click on a share, and click Properties).

---

### Post by adyroman on 2008-09-13
On my computer, if I go to any folder, right click it and share it from "Sharing", then open "shares-admin", the share doesn't turn up there. I can only assume that shares-admin shows the shares from /etc/samba/smb.conf, although I haven't tested that. My question was, where does Nautilus keep its shares list???... I think it's extremely unlikely that Nautilus uses anything else than Samba for file sharing, and then if it uses Samba, how does it tell Samba to share those folders?

Going back to my problem - if I have a shared folder and I no longer remember where it is located on the file system, how do I unshare it?

---

