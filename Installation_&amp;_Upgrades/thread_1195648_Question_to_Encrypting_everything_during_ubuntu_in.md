---
title: "Question to: Encrypting everything during ubuntu installation"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by matthias24 on 2009-06-24
Hi,

I already made an encrypted installation on my previous computer where I had just 1 HD. I first created the encrypted partion and with LVM I created root /home and swap in it. Worked like a charm.

But now I have 2 discs on my new computer:
1 Solid State Disc 30G
1 SATA 500GB disc 

on the SSD I want to put root and swap and on the 500GB HD I want to put /home

my question is now, how do I configure that without entering a password 2 times at boot time and without mixing the two discs together. I want to use the speed of the SSD disc for root and swap and the slower 500GB disc for my /home. 

By the way: I do NOT want to use truecrypt

I hope someone can help me, thx in advance

---

### Post by dsavi on 2009-06-24
I did this (Or something similar) just two days ago, I'll see if I can find the same tutorial. :P

Here we are; It's not exactly the same but it's very close. It uses nearly exactly the same commands. [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Additionally, if you get an error about chmod permissions when you try to log in again, do this:
Restart and go into recovery mode, select a root shell and type in a root password
```
# chmod 644 /home/[username]/.ICEauthority
# chmod 644 /home/[username]/.dmrc
```
Replacing, of course, [username] with the name of any account that has chmod errors when logging in.

---

### Post by matthias24 on 2009-06-24
> **dsavi said:**
> I did this (Or something similar) just two days ago, I'll see if I can find the same tutorial. :P

Here we are; It's not exactly the same but it's very close. It uses nearly exactly the same commands. [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

thx for the answer but I am not quit sure how this article helps me with my problem:
I need a solution on how I can encrypt 2 harddiscs (on one encrypted harddisc should be my /home on the other  root and swap) and when I boot this encrypted system I do not want to enter a password two times

So maybe there is a way how I can mount the encrypted home partition without entering a password manuelly. Perhaps with a keyfile or so.

---

