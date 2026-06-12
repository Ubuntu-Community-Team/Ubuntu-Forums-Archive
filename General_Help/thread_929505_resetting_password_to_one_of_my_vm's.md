---
title: "resetting password to one of my vm's"
date: 2008-09-25
forum: General Help
---

### Post by Mia_tech on 2008-09-25
I'm trying to reset the password to one of my ubuntu virtual machine which I haven't used in quite a while, and dont' remember the password, but I'm using the recovery mode method, but after I select the "Drop to root shell prompt", I get prompt for the root password, and I don't even know if I set one for the root account when I first installed the vm... is there any way around this?

---

### Post by Elfy on 2008-09-25
You don't need a password at the root prompt. As long as you know the username, to reset the password in root prompt

```
passwd username
```

then enter new password.

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by DagMan on 2008-09-25
He needs to follow the second part of that wiki page as he's getting prompted for the root password to go any further.

---

### Post by DagMan on 2008-09-25
He needs to follow the second part of that wiki page as he's getting prompted for the root password to go any further. 


Edit: Hmm... On second look this was completely useless information :p

---

### Post by Mia_tech on 2008-09-25
I used this guide....I'm still amazed how easy it is for someone with physical access to gain root privileges on the machine... do any of you guys know why ubuntu has not change this approach?

[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html)

---

### Post by Elfy on 2008-09-25
There is more than one thread here on that - somewhere ;)

At the end of the day if someone has physical access they are likely to be able to do anything they want anyway imo. 

I assume that you managed to sort the password.

---

