---
title: "Live Mesh like functionality for Ubuntu?"
date: 2008-09-10
forum: General Help
---

### Post by moschops on 2008-09-10
Is there anything similar in functionality to Microsoft's "Live Mesh" file sharing and remote access technology?  I've been testing Live Mesh on my various Windows machines and found it pretty compelling.  

Yes I know there is ftp, Samba, etc. but it seems that it should be relatively easy to create an equivalent product/service for Linux using a central server, rsync plus VNC (or equivalent).  

A cool addition might be the ability to implement a cached virtual file system so if shared files have not yet been completely synced to remote clients they can still be accessed on a block by block basis from the client.

Say you have 10,000 MP3s to sync up and it will take a while across your slow DSL network connection - why not show all the files as existing on each sync client (there maybe more than one), meanwhile the sync daemon is copying data to the client behind the scenes.  But if one particular file (or block of a file) is needed then start streaming data for that file alone to the client, a kind of a read-through cache. For many purposes, like playing an MP3 you should be able to get the data across fast enough to keep the application reading it happy.

Well just an idea - even a basic easy to use, nice GUI on top of rsync with a central server that is close to Live Mesh would be great.

PS. For similar products on Windoze see Syncability or Sugar Sync.

---

### Post by jcc123 on 2010-02-10
Ubuntu One is the Live Mesh like software you want. Justa Subcribe and you get 2gb storage for free with possible upgrade to 50gb.

---

### Post by commodore256 on 2010-11-17
> **jcc123 said:**
> Ubuntu One is the Live Mesh like software you want. Justa Subcribe and you get 2gb storage for free with possible upgrade to 50gb.

Yeah, but Skydrive has 25GB for free. (as in beer)

Also, your family would be more likely to use skydrive/mesh than Ubuntu One. Despite the fact you can only upload 50GB per file, the only thing that's wrong with it is there's no way to sync a folder on linux.

This would be perfect for sharing photos with family.  I hate how my family uses facebook to keep pictures forever >,< I can't believe they put their memories in thumbnails.

---

