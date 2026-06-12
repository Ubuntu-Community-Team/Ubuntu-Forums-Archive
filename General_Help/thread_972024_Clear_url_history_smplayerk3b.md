---
title: "Clear url history smplayer/k3b"
date: 2008-11-05
forum: General Help
---

### Post by 289Shelby on 2008-11-05
When I open smplayer and select File/Open it opens some kind of search box, I'm not sure what it is. However when I click the down arrow in the url bar it shows a list of local urls some of which have no relation to video. What I'm trying to do is clear this list but cannot for the life of me find out where the list is stored.

I've also found out that opening K3B and selecting File/Open displays the same box with the same history.

Does anyone know what file is being used to store said history or how I can delete it?

Thanks.

This is kubuntu 8.04 btw.

---

### Post by rvm4000 on 2008-11-05
> **289Shelby said:**
> When I open smplayer and select File/Open it opens some kind of search box, I'm not sure what it is. However when I click the down arrow in the url bar it shows a list of local urls some of which have no relation to video. What I'm trying to do is clear this list but cannot for the life of me find out where the list is stored.

$HOME/.config/Trolltech.conf

The history seems to be stored in the line which starts with
```
filedialog=@ByteArray(...
```

---

### Post by 289Shelby on 2008-11-06
Thanks for your reply. Unfortunately that hasn't made any difference.

Rather that delete the existing line I commented it out and added:

filedialog=@ByteArray()

I have to admit that I have no idea what the above means but the history list is still there even after logging out and back in again.

---

### Post by rvm4000 on 2008-11-08
All I can say is that deleting the filedialog line in $HOME/.config/Trolltech.conf makes the history to be deleted in the open dialog in smplayer (0.6.4).

I haven't tested k3b, but as it is a kde application probably that info will be stored somewhere in the kde configuration files.

---

### Post by emarkay on 2010-11-04
Well, a coupl-a years later - anyone have an answer? It's not cleared via any tools I am aware of automatically.  So what is the filename of the K3b history data?

---

### Post by no2498 on 2010-11-05
if i click recent files i can click clear
im using 10.04 lucid

---

### Post by emarkay on 2010-11-11
OK, FWIW, "/home/,username./.kde/share" are a few places that some of this data is found.

---

