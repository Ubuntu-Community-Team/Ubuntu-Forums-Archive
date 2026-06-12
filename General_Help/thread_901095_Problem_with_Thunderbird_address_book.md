---
title: "Problem with Thunderbird address book"
date: 2008-08-26
forum: General Help
---

### Post by hezuo on 2008-08-26
[FONT="Verdana"]Hi there, thunderbird address book works fine when I run it as a regular user, but it doesn't work when i tried to run it as root. I mean, thunderbird works fine, but I can't add or see any contact. Is there any way to solve this? thanks a lot in advance.[/FONT]

---

### Post by Dojan5 on 2008-08-26
The root is another account. It just has privileges to do everything on the computer.
You won't be able to see your posts in the address book since there are no. Why would you want to run Thunderbird as root?

---

### Post by pmlxuser on 2008-08-26
thats because the adreess book is stored in the home folder of every user( ie /home/username/.mozilla-thunderbird/), with such if you run as root you access the adress book of root (/home/root/.mozilla-thunderbird/)which doesnot have anything sor far because you used your other user account.

Anyway how do you rung as root in ubuntu? i have never managed to log in as root i can gain super user powers using sudo in a normal user account. ;)

---

### Post by Dojan5 on 2008-08-26
> **pmlxuser said:**
> thats because the adreess book is stored in the home folder of every user( ie /home/username/.mozilla-thunderbird/), with such if you run as root you access the adress book of root (/home/root/.mozilla-thunderbird/)which doesnot have anything sor far because you used your other user account.

Anyway how do you rung as root in ubuntu? i have never managed to log in as root i can gain super user powers using sudo in a normal user account. ;)
With a risk of going off topic.
You can run applications as root, however I do not know how to login as root.
My guess is that He/She runs Sudo Thunderbird or something.

---

### Post by pmlxuser on 2008-08-26
> **Dojan5 said:**
> 
My guess is that He/She runs Sudo Thunderbird or something.

do you know why somebody would do that??

---

