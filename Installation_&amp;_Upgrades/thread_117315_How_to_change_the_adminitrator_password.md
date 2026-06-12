---
title: "How to change the adminitrator password ?"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by shankumaran on 2006-01-14
HI All,

Accidently, I forgot my administrator user password. But I have an another user account, with that I could able to login but, when I try to change my password using the following command

sudo bash

The system says, "unable to look up public/pickup: No such file or directory"

Thanks,
Shan

---

### Post by Zelut on 2006-01-14
...not sure where you got 'sudo bash' to update the password :)  Try this:

sudo passwd root (for roots password) and it'll prompt you for a new one.  If you don't have permissions to do that however you may be stuck..

---

### Post by shankumaran on 2006-01-14
Thanks for the reply....

I am still getting the following message...do you guess what is the problem

unable to lookup <currentUser> via gethostbyname()

---

### Post by fireonyx on 2006-01-14
I had the same problem there... take a look at my thread to figure it out... [http://www.ubuntuforums.org/showthread.php?t=117019](http://www.ubuntuforums.org/showthread.php?t=117019)

---

### Post by shankumaran on 2006-01-14
Hi fireonyx,

Thanks for your reply...it looks like your problem is not related to the administrator password. I am trying to reset my admin password.

Can you tell me atleast, how I can update the ubuntu..? with out being a adminitrator ?

I am also very new to Ubuntu...trying to play around 

Thx

---

### Post by fireonyx on 2006-01-14
lol, I am very new as well...  What I did at least allowed me to use sudo, where I got the same problem you did...  use the recovery mode when you first boot up, that will log you in as root...  you may be able to do your sudo passwd root from there.

---

