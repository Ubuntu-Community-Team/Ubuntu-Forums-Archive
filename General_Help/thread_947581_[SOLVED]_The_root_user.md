---
title: "[SOLVED] The root user"
date: 2008-10-14
forum: General Help
---

### Post by fs_tigre on 2008-10-14
Hi,

I was reading something about linux for beginners and they recommend not login as the root user but…  What is the root user?  Is this the first user specified when installing the OS?

Why not use it?

Can someone explain this a little bit more please?

Thanks,
Fs_tigre

---

### Post by Sam on 2008-10-14
Read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fballem on 2008-10-14
The root user is the user named 'root'. On most Linux distributions, you can log in as root to do system administration activities.

In ubuntu, the root user is disabled by default. The first user that you define on the system is allowed to do administrative activities, but normally does not operate as the administrator.

In order to do administrative activities in ubuntu, you would execute 'sudo' or 'gksudo' from a terminal, at which point you will be asked for a password - which would be your own password.

Administrative utilities, like Synaptic, are designed to take this into account - that's why you are asked for your password when you select these.

If you look at various posts, such as this one: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683), you will see a lot of instructions that start with the word 'sudo' (short for superuser do, I think). If you do one of these commands, then you will be asked for a password, which will be your own.

Please be very careful in following instructions when operating as superuser - you can do a lot of damage. Most of the posts in this forum, from my experience, will tell you what it is that you are to do and why. Read carefully to make sure that you understand, and if you don't understand, then please ask before you do it.

Hope this helps,

p.s. I posted this at the same time as the user who posted the link to the documentation. Think of mine as the 'short explanation', but I would strongly encourage you to read the document that is provided in the previous post.

---

### Post by overdrank on 2008-10-14
Hi and for the forums policy on the root applications pleas view
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by fs_tigre on 2008-10-14
First of all thank you very much to all, this is a nice forum.  Nice explanation fballem!!!!:)

---

### Post by fballem on 2008-10-14
Just a suggestion - if you are satisfied that you have the information you need, you may want to mark this thread as Solved, so that others can benefit.

If you look at the top, you will see Thread Tools. One of the options is to mark the thread as solved.

This will help others.

Regards,

---

