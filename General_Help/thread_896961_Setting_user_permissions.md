---
title: "Setting user permissions"
date: 2008-08-21
forum: General Help
---

### Post by lsutiger on 2008-08-21
I have a project I am working on where I will need to make the permissions for other users extremely basic, IE - not be able to setup software, no use of internet applications (but being able to login remotely via X - Is there a better solution than just X?). 
In the end, I just need these users to able to access their home folders remotely, be able to view OO Docs and thats it.

Whats the best solution here?

Thanx for the input!

---

### Post by tuxulin on 2008-08-21
i would not allow untrusted or trusted user(s) to login via x
to me i think its a bad plan.

i have ssh test server and i log in via x and cli the problem is this. 
the remote user has certain amount of control
over the system and in addition to this he/she has the ability to
browse all of your mounted drives :(

i dont know if there are any real easy way to lock a remote down to
solely there home directries.

even using chroot or Jailkit (i think thats what you need) is a pain to properly setup and configure all though it can be done and when completed does work effectively.

example just imagine a remote user logs in and at the cli types
nautilus (if connected via x)

Good Luck
Tuxulin

---

### Post by spiderbatdad on 2008-08-21
There is some information in the Ubuntu Handbook that might pertain to what you want to do. You can download it for free as .chm then convert it if you don't have windows.
It talks about partitioning schemes and setting rules in /etc/security/limits.conf. It's basically about system administration for multi-user systems

---

### Post by lsutiger on 2008-08-24
Thanx for the input. I think I have found an answer at nomachine.com.
I just need to set permissions for the users very, very low.

I will d/l the handbook and may even setup ubuntu server (is there a link to the 7.10 version anywhere??)
Thanx again!

---

### Post by lsutiger on 2008-08-24
Does anybody know where to get the ubuntu handbook?

---

