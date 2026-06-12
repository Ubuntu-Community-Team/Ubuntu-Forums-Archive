---
title: "Are root immune processes possible?"
date: 2008-11-23
forum: General Help
---

### Post by RFXCasey on 2008-11-23
Is it possible to set a process so that even root can't kill it. Or better yet is there a way to make a command, lets say Stop for instance, password protected with something other then the root password. Asking why I would want to do this is irrelivent so don't bother.

---

### Post by lswb on 2008-11-23
I don't believe you can keep root from killing any process, however for your second question, you could compile your own password/response code into the program itself.

---

### Post by GuitarRocker2562 on 2008-11-23
It would be a major security flaw if it worked, so I am sure it doesn't.

---

### Post by jimmy the saint on 2008-11-23
there really is no good reason to want that, at least none that I can think of.  The whole point of the administrator account is to be able to administer the machine.  If the process should not be killed, the admin shouldn't kill it.  Linux is not M$.  If someone figured out how to do this, I'm sure the new "feature" would be quickly fixed.

---

### Post by DGortze380 on 2008-11-23
Sure. Root can do anything it wants.

Of course... root can also change back anything it wants.

So while the answer is technically 'yes'... practically the answer is no.

---

### Post by RFXCasey on 2008-11-23
I need to know if there is any way to prevent root from stopping a process or application. Or better yet is there a way to password protect a command like the "Stop" command for instance with something other than the root password so that even root can't use it without knowing the password. Please don't bother to ask why I would want to do this as this is irrelivent.

---

### Post by spiderbatdad on 2008-11-23
never tried it:
[http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html](http://linuxhelp.blogspot.com/2005/11/make-your-files-immutable-which-even.html)

---

### Post by bodhi.zazen on 2008-11-23
> **RFXCasey said:**
> I need to know if there is any way to prevent root from stopping a process or application. Or better yet is there a way to password protect a command like the "Stop" command for instance with something other than the root password so that even root can't use it without knowing the password. Please don't bother to ask why I would want to do this as this is irrelivent.

Threads merged, please do not start multiple threads on the same topic.

It would help if you were to describe what you are doing. root is the ultimate administrator and :

1. First, a user can not stop processes started by other users or root without root access.

2. If you have multiple administrators, you can configure sudo to give access to some but not all commands to other admins.

3. Otherwise, no, root = the ultimate administrator. The closest you could come to something like this would be SELinux, but ever with selinux, if someone logs in as the root sys admin role they will have access to stop processes.

---

### Post by sarang on 2008-11-23
No, root-immune processes are a terrible idea and would defeat the meaning and purpose of super-user privileges. By well thought UNIX design, the SIGKILL signal that root can issue to any process cannot be trapped by the process and will cause a _possibly unclean_ forced termination of the process. Some very old versions of *nix had a flaw due to which by extremely clever use of zombie and orphan processes, some amount of root immunity could be achieved for a short time. However I believe that this is impossible now.  

Files that can not be deleted by root can be created on ext2/3 filesystems by setting the so-called 'immutable' bit on the file, but that requires super-user privileges and can be undone easily by someone with super-user privileges. However in any case, this concerns files (more precisely, inodes) only; I believe nothing of this sort can be achieved with processes. I will reconsider my choice of operating system if you can show me that I am wrong. BTW, I do not recommend setting the immutable flag on anything.

If you have an overly pesky root user, I think your best bet is to name your process something innocuous so that it does not stand out in the ps output and thus the chances of root not killing it are increased.

---

