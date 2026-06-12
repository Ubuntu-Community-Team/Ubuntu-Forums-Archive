---
title: "root password too easy?"
date: 2008-08-28
forum: General Help
---

### Post by Breakar on 2008-08-28
When i first installed ubuntu it asked for a password and i made it really easy, i was just wondering if its a security risk online and should i change it?

---

### Post by tuxxy on 2008-08-28
Dont tell me, you used root :lolflag:

---

### Post by jonian_g on 2008-08-28
Mine is the easiest you can think but I never had any security problems and I use the same pass for 2 years or more.

I don't know though if it is realy a security problem having set an easy password.

---

### Post by mb_webguy on 2008-08-28
It shouldn't be a security problem unless:

A) you have other security problems, such as an open port a hacker could use to access your system, or
B) you're on a multi-user system, or
C) you allow other people to have unsupervised physical access to your computer.

Things like web servers, ftp servers, or game servers open ports on your system, and these open ports may possibly be used to access your system.  This access (and more specifically any security exploits that associated with the programs that use these ports) is the primary problem, but an easy root password just makes things easier for a hacker after he initially gains access.  It's a bit like leaving your front door open when you leave the house, and leaving a set of keys laying on a table next to the door.  Leaving the door open is the primary problem, and the keys make it easier to get back into your house later, and possibly take your car.

This isn't to say that it's ok to have an easy root password.  It's best to have a strong password using a combination of letters, numbers, and (when possible) special characters, especially in situations (such as multi-user systems or a shared apartment) where other people might have access to your system such that they might have the ability to find out and use your password.

---

### Post by mssever on 2008-08-28
It's best to disable the root password (as is the Ubuntu default), since there exists no situation in which it's needed (or even more convenient), and you can't guess a nonexistent password. Use sudo -i if you really want a root shell. To exploit a password to break into a machine, you need to know both the username and the password. Since virtually every Linux box has a superuser account called root, that part's easy to guess, and you can increase the difficulty by not allowing root to have a password.

If untrusted people have physical access to your machine, or if you run any kind of server (such as sshd), then you need a strong password on your user account.

---

