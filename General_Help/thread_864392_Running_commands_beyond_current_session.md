---
title: "Running commands beyond current session"
date: 2008-07-19
forum: General Help
---

### Post by spitzanator on 2008-07-19
So, as I understand it, you can only run commands within your session.  For example, when I login and run rsync, if I log out, I necessarily kill that rsync process.

What I'd like is to be able to start a program remotely (like a music player), log out and have it persist, and then be able to log back in later and have access to that process again.

I know that for Java, there exists the Apache Commons Daemon (formerly JSVC) that allows you to spawn Java processes that persist until you send the arguments to kill them, but I'm wondering if a generic version of this for *nix.

Does something like that exist?

Thanks!

-Matt

---

### Post by rossjman1 on 2008-07-19
Have you tried running the commands as root?

---

### Post by hyper_ch on 2008-07-19
if it's CLI stuff you can use the "screen" program

---

### Post by ddales on 2008-07-20
For something like an rsync, you should take a look at the "at" command.  I use it a lot at work.

---

### Post by spitzanator on 2008-07-21
hyper_ch>  That's exactly what I wanted, thank you so much!

ddales> Not what I was looking for but certainly useful.  Thanks!

---

