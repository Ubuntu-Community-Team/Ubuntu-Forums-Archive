---
title: "Can I run a program in the local session remotely from SSH?"
date: 2005-11-30
forum: General Help
---

### Post by matthinckley on 2005-11-30
OK This one may be wierd but I've searched around and couldn't find anything..  I am logged into my computer at home and what I would like to find out is if there is a way I can log in with SSH and start a program in my X session that is running at home from the SSH terminal.. I don't want to take over the desktop with vnc.

Is this possible.. like maybe a command to tell linux that I want this program started in tty7 or something like that.. I'm kind of a newbie.

Thanks in advance

Matt

---

### Post by soulestream on 2005-12-01
[http://www.xs4all.nl/~zweije/xauth.html](http://www.xs4all.nl/~zweije/xauth.html)

[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)


might help depending on what you are doing


soule

---

### Post by jliedeka on 2005-12-01
You might try changing you DISPLAY environment variable to ":0.0".  That is, if you are trying to get the X program to run on your home computer.  I'm not sure why you'd want to do that but there it is.

If you want to run an X program remotely and have the display be the machine you are on, connect with "ssh -X" and all the X stuff should get forwarded to the X server where you are.

---

