---
title: "Sharing folders over a LAN"
date: 2008-08-15
forum: General Help
---

### Post by Roger D on 2008-08-15
Hi

I've got two 8.04 PCs on the same wireless LAN. Is there some simple way I can share folders between these two machines?

Roger D

---

### Post by iaculallad on 2008-08-15
> **Roger D said:**
> Hi

I've got two 8.04 PCs on the same wireless LAN. Is there some simple way I can share folders between these two machines?

Roger D

Had you tried System->Administration->Shared Folders?

---

### Post by Roger D on 2008-08-15
I don't have Shared Folders under System>Administration.

Funny that, I'm sure it was there under 6.06

---

### Post by jerome1232 on 2008-08-15
> **iaculallad said:**
> Had you tried System->Administration->Shared Folders?

That's not in 8.04 anymore, you have to right click a folder click sharing options, click share this folder. then it will install some stuff for you.

Personally though I like to use SSH to share files, install openssh-server and sshfs.

Click places>>connect to server, select ssh, fill in the blanks and hit connect. You should now have the filesystem mounted on your desktop.

---

### Post by Roger D on 2008-08-15
Hmm... Thanks. I never got Shared Folders to work anyway. Being a bit simple-minded about these things, I had this idea that I would be just able to 'see' the two file structures in some way, and drag folders between them..

I guess it's not to be

---

### Post by jerome1232 on 2008-08-15
You can do that using both of the methods that have been described (one using samba the other ssh) 

Right now I'm browsing the contents of my server and I can click and drag files into/out of the server.

---

