---
title: "giving NIS user admin privileges"
date: 2005-12-02
forum: General Help
---

### Post by dccarson on 2005-12-02
I'm new to Ubuntu but not to Linux.  This whole sudo thing is giving me some grief due to my need for NIS login -- hoping someone can help me out.

I created a user during install, call it uburoot, the sole purpose of which is to run admin commands from the system admin menus.  I do not plan to login as this user normally, since I am in an NIS environment.  (I promptly changed the root password too, since I want to have that control.)

Now that I've gotten NIS working, I finally logged in as myself (not root or uburoot).  The $64 question is: How do I grant my NIS-based account admin privileges for the system menus?   I found the help that suggested going to "Users and Groups" and adding "Executing system administration tasks" for this user, but the problem is that the NIS users do not show up in this list.

Whenever I do admin tasks from the command line, I will just su to root.  But I'd like to be able to do some admin from the menus too, and I don't want to have to logout as myself and login as uburoot every time.

Thanks,
David

---

### Post by caplod on 2005-12-02
you could add yourself to the /etc/sudoers file.

---

### Post by dccarson on 2005-12-02
Thanks, that did the trick.  I knew it was simple!

---

### Post by ideasman42 on 2007-10-06
Hey, I had this same problem, and the solution works fine.

however is it possible to give users admin privilidges (such as the ability to sudo on their own PC) but NOT on the server?

Because I dont want them to be able to ssh into the server for instance and browse all the files.

---

