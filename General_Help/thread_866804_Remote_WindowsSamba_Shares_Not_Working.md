---
title: "Remote Windows/Samba Shares Not Working"
date: 2008-07-22
forum: General Help
---

### Post by airjrdn on 2008-07-22
Ubuntu 8.04 can't seem to see them.  Sometimes after reloading Nautilus a couple of times, the servers show up in Network, but I can't view the shares.  I have at times, but it's not at all consistent.

WinXP via VirtualBox can view & use them fine though.

To get sound working, I had to recompile my kernel as shown [here]("http://ubuntuforums.org/showpost.php?p=4823915&postcount=675") if that matters.

---

### Post by cprofitt on 2008-07-22
How are the shares setup on Windows?

What are the share permissions?

What are the NTFS permissions?

---

### Post by airjrdn on 2008-07-22
There are different groups with varying access to the different shares, but I'll refer specifically to one in particular.

Apps Admin is a group with full rights to the Apps Share.  The same user I login and password to Ubuntu with exists on the fileserver and is in that group.

That same user has full NTFS rights to that entire drive.

Does that tell you what you need to know?

---

