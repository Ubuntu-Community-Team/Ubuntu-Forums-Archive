---
title: "Need Help With Rsync"
date: 2008-10-03
forum: General Help
---

### Post by bhoemen on 2008-10-03
i'm new with the whole linux and need help setting up rsync to update the ubuntu 8.10 beta iso file

---

### Post by ajmorris on 2008-10-03
> **bhoemen said:**
> i'm new with the whole linux and need help setting up rsync to update the ubuntu 8.10 beta iso file

hi there,
im not sure i completely understand what you are trying to do. Rsync is a tool to copy over data, i.e. a backup tool. If you are trying to update your ubuntu to 8.10, you need to edit your repositories in /etc/apt/sources.list then do an apt-get dist-upgrade. (you can use your iso file, mount it, and use it as a repository) However, if you are new to linux, i do not advise upgrading to 8.10, it is still beta as you mentioned, and with betas, comes bugs, you would have to deal with broken packages and system on a daily basis.

AJ

---

### Post by bhoemen on 2008-10-11
When you test the ISO releases, you are unfortunately faced with the task of downloading a new set of ISO images every two weeks. This can take up a lot of bandwidth, and is absolutely out of the question for dial-up users. You can drastically reduce the amount of bandwidth your iso downloads take by synching the images using a protocol known as rsync.

I'll edit and incorporate this document later, but for now, here is a link to it: Using rsync to update Mandriva Linux ISO Images 

you can use rsync to update mandriva

---

### Post by niteshifter on 2008-10-11
Hi,

The missing link that bhoemen didn't provide ;) is a dead page - but is available in Google's [cache]("http://64.233.169.104/search?q=cache:2hyy-l0tQDgJ:cybercfo.gkmweb.com/rsync-mandrakeiso-old.html+Using+rsync+to+update+Mandriva+Linux+ISO+Images&hl=en&ct=clnk&cd=5&gl=us").

It might be useful in aiding you setting up rsync. So will the man page on rsync.

Instead see [here]("http://www.ubuntu.com/getubuntu/mirror")(ubuntu.com). That page links to a list of mirrors.

Make sure you're rsyncing to just the needed ISO, not an entire archive! That'll will A) really annoy your ISP, B) Take days, if not weeks even on 6 or 8 Mbs connections. We're talking 100's of GB on a full Ubuntu archive.

---

