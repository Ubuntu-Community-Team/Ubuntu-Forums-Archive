---
title: "Hibernate"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by Suppermann on 2009-10-19
Hello

I recently installed ubuntu 8.04 from debian lenny. I did a net install, and i accidently hit enter while choosing what 'packages' i wanted. That meant i had to install everything manually (such as Xserver, gnome, firefox...).
One day I wanted to hibernate my laptop, but I could only shut it down or suspend it (suspend doesn't work, I think it's something with my graphics card). Then I typed sudo aptitude install hibernate and tried that. It didn't work, no explanation.

Anyway, I need help hibernating my laptop

Thanks for the help, in advance.

Suppermann

---

### Post by Suppermann on 2009-10-19
Additional information:
When I try sudo hibernate, the screen goes weird, like when I'm switching from tty1 to display :0, for example. And then nothing. When I press Quit... in System, I don't get the option hibernate.
EDIT: It worked in Lenny, so it's probably nothing to do with my hardware (at least it's possible, I think).

---

### Post by Mark Phelps on 2009-10-21
Hibernation is a particularly difficult problem to solve in Linux.

You would probably get more info if you went to the laptop subform and did a search on the term "hibernate" and your laptop model.  That will at least show if others have attempted the same thing and succeeded.

---

### Post by Suppermann on 2009-10-22
I have now searched for my laptop on all the support forum with no result (note I didn't even include hibernation. I only searched for d7820, because my laptop is an fujitsu-siemens amilo d7820). I don't think this should be a big problem to solve, because it worked out-of-the-box in Debian Lenny.

---

### Post by Suppermann on 2009-10-22
Okay, I have just found a log in /var/log/hibernate.log. It says that after about 2 seconds or so, it resumes after hibernating. Which sounds quite silly. Does this help?

---

### Post by Suppermann on 2009-11-02
Upgrading to 9.10 fixed everythin. Even suspend works now! It didn't work in any of the previous versions/dists I have tried.

---

