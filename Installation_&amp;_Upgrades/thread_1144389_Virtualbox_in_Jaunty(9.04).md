---
title: "Virtualbox in Jaunty(9.04)"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by vaughnm on 2009-04-30
So I just downloaded Virtualbox and got it going.
I downloaded it from the website (version 2.2.2) 
The thing is my drive is already partitioned.
The other problem is windows won't start natively. 
So...getting into windows to edit my guest account is not an option.

How can get VB running with an already partitioned drive?

There are similar posts but they are for 8.04

Who's got a good answer for me?

---

### Post by smudi on 2009-04-30
I don't quite understand what you are trying to achieve
Running a guest windows box on an jaunty host?

---

### Post by vaughnm on 2009-04-30
Well it's not that I'm trying to run a guest account. But what I've seen is that you need to edit your guest account somehow in Windows. If this is wrong I would like to know how to do it properly.
What I'm trying to do it run VB on my computer that already has the drive partitioned. 
But, I can't start XP natively.

All I want to do it run VB on ubuntu but I don't know how to do it without running windows natively at some point.

---

### Post by smudi on 2009-04-30
I think you got some of the definitions mixed up.

Hope this helps:
[http://seogadget.co.uk/how-to-install-virtualbox/](http://seogadget.co.uk/how-to-install-virtualbox/)

---

### Post by vaughnm on 2009-04-30
Ok, well thats a good post, thanks for sharing. 
It doens't really solve my problem.
My issue is I don't want a fresh install. I already have windows running on my computer and I want VB to recognize it.
I don't have a windows cd either so thats another issue.
How can I get Vb to recognize that I already have windows running on my computer?

---

### Post by Gary Stout on 2009-04-30
Vaughnam,

Unless the version of Windows is from a previously installed VB session, I don't think it is possible to make a native version of Windows work. VB creates an image of Windows (*.VDI) file and that is what VB would look for to run Windows. If you are running a dual boot setup, VB won't work like that. 

I probably didn't explain that very good, but hopefully you can make some sense out of it.

Gary

---

### Post by Shazaam on 2009-05-02
Have you looked at this?
[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

Make sure you read the ENTIRE thread.

---

