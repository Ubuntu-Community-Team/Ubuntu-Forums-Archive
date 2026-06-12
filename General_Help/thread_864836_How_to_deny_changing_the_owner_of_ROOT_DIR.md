---
title: "How to deny changing the owner of ROOT_DIR"
date: 2008-07-20
forum: General Help
---

### Post by bogdanbiv on 2008-07-20
How can I set up a policy that denies users (root too) to change the owner of / and /opt, /usr ... (all level 1 child directories)
Also one for chmod and file/directory deletion also for / and subdir.

Is it complicated?

I would like to block it since it's the second time I nearly trashed my system by changing ownership of directories recursively (resulting in /usr being owned by my limited access user).

---

### Post by sdennie on 2008-07-20
I don't think this is possible.  The root user can do whatever it wants regardless of permissions.  My advice would be to use the "ls -R" before doing any sort of "chmod -R", "chown -R" or "rm -r" to make sure what you are about to do isn't going to trash your system.

---

### Post by bogdanbiv on 2008-07-20
I will try to educate myself to that - but you know it's easier to teach the computer than the user, right? 

Thanks, vor! :-)

---

### Post by sdennie on 2008-07-20
> **bogdanbiv said:**
> I will try to educate myself to that - but you know it's easier to teach the computer than the user, right? 


True.  In that case, one other thing you could try would be to disallow yourself the ability to use rm/chmod/chown as root via /etc/sudoers and instead force yourself to use a script that runs an "ls" and asks for confirmation before doing the operation (sort of a "safe_rm").  That's sort of an extreme measure though and I'm not sure exactly how you'd set it up.

---

