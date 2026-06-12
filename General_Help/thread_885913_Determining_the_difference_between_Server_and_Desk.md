---
title: "Determining the difference between Server and Desktop"
date: 2008-08-10
forum: General Help
---

### Post by billmc on 2008-08-10
Can some one explain to me what process takes place that distinguishes a desktop distribution from a server distribution?  I'm interested in the Long Term Support distros, in particular 8.04.

Recently I began building a couple of production boxes that I want to be able to receive updates for.  I anticipate these being in use for quite some time, maybe even longer than the 5 year support offered to the server.

I started with a minimal server install and added packages that I needed.  It suddenly dawned on me, at least as far as I can tell, the only difference between the server and the desktop is the kernel that is being used.

I'm thinking about using the 2.6.26 kernel for a feature that has come available, read only bind mounts ( see this article  [http://lwn.net/Articles/281157/](http://lwn.net/Articles/281157/) ), when it occurred to me that if it is the kernel that is being used to differentiate between server and desktop, and I changed, that I could no longer expect to receive the long term updates.

If some one could explain to me how this operates, I'd really appreciate it.

Bill

---

### Post by damoxc on 2008-08-10
I would imagine that only the packages that would be used on a server will continue to receive updates, ex. webservers, ftpservers and so on. None of the desktop packages would receive any.

---

### Post by sdennie on 2008-08-10
You can use a custom kernel and still receive long term support for the machine.  It just means that keeping the kernel up to date with security patches and such becomes your responsibility.  I believe that the difference between the server and desktop is just that the core server apps will continue to be updated after support for the desktop environments has ceased.

---

### Post by Separ on 2008-08-10
I think I heard somewhere that by default, the server version comes with no GUI and if you want one, you have to install it manually.

---

