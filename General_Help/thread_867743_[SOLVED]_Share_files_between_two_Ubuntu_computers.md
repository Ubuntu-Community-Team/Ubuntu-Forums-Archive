---
title: "[SOLVED] Share files between two Ubuntu computers"
date: 2008-07-23
forum: General Help
---

### Post by neur0 on 2008-07-23
OK, I've used the search function, tried googling, and I still can't find the answer.
Whats the simplest way to share files between 2 computers running Ubuntu in a switched environment?
I'm sure theres a how-to for this common task, but I cant find it.
If the answer is SSH, then I can do it, but it doesn't need to be secure (switch).
If I try to just r-click and share a folder, Ubuntu prompts me to install Samba, but I don't want to share files with Windows platforms, and fear that this could be unnecessary and open a vulnerability. Should I just install Samba?

---

### Post by ookamisan on 2008-07-23
The easiest way would really be SCP / SSH, even if you don't need the security. I don't think it adds that much overhead.

The other ways are:
- Setting up an FTP server
- Setting up an NFS server

The latter I never did but FTP is... not that difficult. But anyway, SSH is even integrated into Nautilus, so it really is the easiest way.

---

### Post by neur0 on 2008-07-23
Ok, thanks, I've solved it with SAMBA after reading the discussion on Ubuntu brainstorm. 
Obviously there is NO easy/streamlined way to this at the moment.
It was easy to setup for me, just thought there is some other Linux-only way to do this like there is on other OS. Oh well, soon I'll install a file server on an old computer so it shouldn't be a problem then.
Now, with Samba, my only concern is the security. 
(and why the normal user can't see that the folder is shared when viewing the share tab)

---

### Post by ookamisan on 2008-07-23
Where is your security concern with that? One more port open?

---

### Post by neur0 on 2008-07-23
Basically its the ONLY port opened, however, I'm behind a router (NAT) with firewall on (incoming connections) so it doesn't concern me in this particular case. Next time, I'll solve it with SSH (and open the port on the router), still open port on a public network, but at least I know how to make it more secure.

---

### Post by kevin79 on 2008-10-29
> **neur0 said:**
> Ok, thanks, I've solved it with SAMBA after reading the discussion on Ubuntu brainstorm. 
Obviously there is NO easy/streamlined way to this at the moment.
It was easy to setup for me, just thought there is some other Linux-only way to do this like there is on other OS. Oh well, soon I'll install a file server on an old computer so it shouldn't be a problem then.
Now, with Samba, my only concern is the security. 
(and why the normal user can't see that the folder is shared when viewing the share tab)

Did you have to do anything special with samba? I can't get it working between my two *buntu boxes, but I can access the samba shares from a Windows workstation.

---

### Post by MarcG on 2008-11-12
Everything I've seen so far says to r-click to get the sharing options. But when I r-click, there is no sharing function, and no sharing tab in Properties. I'm running Xubuntu, with Thunar as the file manager.

What do I need to do to share?

--Marc

---

