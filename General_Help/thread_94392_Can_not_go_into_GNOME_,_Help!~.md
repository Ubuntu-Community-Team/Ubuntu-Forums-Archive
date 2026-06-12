---
title: "Can not go into GNOME , Help!~"
date: 2005-11-23
forum: General Help
---

### Post by sisiwong on 2005-11-23
:confused: 

Maybe is the way I installed chmsee wrong??


chmsee cannot be directly installed by dpkg cause of different editions. And to let the edition of libgkhtm down is neither realistic. So I used another way.


I used breezy, which defaulted the edition of libgkhtm is 3.8-15, If your do not use this edition, usr/lib/libgtkhtml-3.8.so.15 does not exist, so you have to change to the suitable edition.

Then I have downloaded a 0.9.5 chmsee. And then run it :

Code : dpkg -x chmsee_0.9.5-1_i386.deb ~ 
~/usr/bin/chmsee 

Waiting for look if chmsee works.

---

### Post by RAOF on 2005-11-23
I'm not sure that I understand what the problem is.  Is the problem:
"I cannot login to Gnome", and if so, what happens when you try?  What errors are there?

What is chmsee?  What does it do?  Where did you get the .deb for it?  Is there not a version of it in the repositories?

---

