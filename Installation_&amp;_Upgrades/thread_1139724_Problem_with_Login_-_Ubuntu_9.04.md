---
title: "Problem with Login - Ubuntu 9.04"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by axou1 on 2009-04-27
Hello, 
 
After upgrading from 8.10 (without any problems), I was asking to input my login and
password to enter 9.04.
 
But my login seems to be not recognize. Meanwhile, I am sure of my login.
 
I control it with ctrl + alt + F1 with confirm it.
Maybe my password but I am also sure of it.
 
Did anyone meet this kind of problem and who have a solution??? 
 
:(

---

### Post by Sam Lars on 2009-04-28
So it tells you that you put something in wrong when you know you didn't?
Can you type your password in as the username (so you can see it) and make sure it's typing what you want it to?

---

### Post by zjagannatha on 2009-04-28
I'm having a similar issue, except when I boot my computer, it won't do anything after I press return. So...

I type my username, hit tab. Type password, hit enter. It acts like it's trying to check the password, but it does it for a long time. (I let it run for 30 minutes).

---

### Post by mafait on 2009-05-06
After installation of 9.04 - I could not login either. I am sure I used the correct user name and password.

I found this remedy: Use a short simple password during installation - **without special characters** - and change the password later.

There is surely a bug in that area during installation. Where can I report this?

---

### Post by meindian523 on 2009-05-06
GUI login or CLI?

---

### Post by mafait on 2009-05-06
GUI login.

I installed 9.04 from inside Windows. (Sorry, I am still a part-time Windows user.)

[U]In steps:
[/U]- Inserted the Ubuntu 9.04 installation CD inside Windows XP SP3;
- Installation GUI was started;
 - Selected another partition and size;
 - User name was already filled in. I agreed with it. So, changes there;
- Entered a strong password and the confirmation;
- During installation no problem was mentioned;
- On first login - the combination of the user name (remembered from installation GUI) and the strong password failed.

After a few unsuccessful retries - I entered the weak password 'kaas' and... presto! It worked fine. I changed my password and the next login was OK.

---

### Post by meindian523 on 2009-05-06
hmm.I had a problem logging in on the CLI,but it was a simple matter of toggling the NumLock (I'm partial to the number pad) and everything worked fine.

EDIT:
No need to apologise for being a Windows user. :D

---

### Post by mafait on 2009-05-06
I found the problem: A strange keyboard setting was installed !!!!!

That's why a strong password fails during the first login.

I didn't had that problem with the installation of 8.04.

Still my advice: Use a weak password during installation.

---

### Post by sahabcse on 2009-05-06
similar problem but different [solution]("http://sahabm.blogspot.com/2009/04/segmentation-fault-unable-to-login.html")

---

