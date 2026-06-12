---
title: "can't su: authentication error"
date: 2005-11-16
forum: General Help
---

### Post by ralph4100 on 2005-11-16
I'm trying to install xampp. the first instruction is:  ```
su
``` in the prompt. When I do, I get an authentication error. I'm *brand new* to linux, so first of all, I don't even know what su does. Second of all, do you know why I would get an authetication error? I found this site, but wasn't sure if it was my solution: [http://www.linuxquestions.org/questions/archive/13/2005/08/1/323274](http://www.linuxquestions.org/questions/archive/13/2005/08/1/323274)

thx

---

### Post by ralph4100 on 2005-11-16
btw it's not because the password is wrong...

---

### Post by Kyral on 2005-11-16
The Root Account is disabled by default in Ubuntu, so su won't work. For the time being
```
sudo -i
``` will have the same effect. The password is your user password. But please read

wiki.ubuntu.com/RootSudo

---

### Post by mrquick on 2005-11-16
if you want to actually use the root account as you would in any other distribution.  You can sudo passwd root.  Give the root account a new password, and then you should be able to su to it from there.

---

### Post by kruz on 2005-11-16
not to mention you have to go into the user account manager
and make sure the login screen enables root login
if ur gona use  x, besides terminal

---

### Post by Kyral on 2005-11-16
DO NOT LOGIN TO THE GUI AS ROOT!!!

I cannot stress this enough! Don't go to root unless you know what you are doing. Its easy to completely kill your system. This is why I advocate Sudo over enabling the Root Account (aside from that in Ubuntu enabling the account tends to mess up the GUI System Admin tools)

---

### Post by bonzodog on 2005-11-16
Speaking as an advanced user, I cannot stress the importance of not logging into the GUI as root. Please listen to Kyral.

---

