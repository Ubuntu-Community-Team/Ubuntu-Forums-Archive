---
title: "[SOLVED] Terminal Problems"
date: 2008-10-21
forum: General Help
---

### Post by Kenza on 2008-10-21
When i type in "SU" on my terminal it asks for a password, although when i am typing it in the cursor doesn't move at all and when i'm done typing it in:

desktop:~$ su
Password: 
su: Authentication failure

At first i thought it might be a Caps Lock or Insert key problem, but i eliminated those...really weird that everything else i type shows up and if i remember right when i used to do it, the cursor would at least move to show i was typing in something. I am the only user on this computer, made the password when i did the fresh install and have never changed it.

---

### Post by mikewhatever on 2008-10-21
Well, first the cursor is not supposed to move, although a lot of users would expect it to, so that's ok.
The reason you get authentication failure is because the superuser account is disabled in Ubuntu. You can use sudo su to get admin privileges that don't time out, just don't forget to type exit when you are done.

---

### Post by Dr Small on 2008-10-21
Greetings,
Please read this:
[http://psychocats.net/ubuntu/passwordinterminal](http://psychocats.net/ubuntu/passwordinterminal)

---

### Post by Kenza on 2008-10-21
Awesome, thanx =) so easy yet i been working on figuring it out for over an hour! Appreciate the Re:!!!

Problem Solved =)

---

### Post by tuxxy on 2008-10-21
You should be typing your root password if you enabled it

---

