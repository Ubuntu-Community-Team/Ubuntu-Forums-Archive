---
title: "Help Connecting to Remote Ubuntu Computer"
date: 2008-11-07
forum: General Help
---

### Post by adlin5000 on 2008-11-07
I have built a computer for a friends mom and installed Ubuntu on it. They have just now gotten internet access. I would like to set it up where I can connect to their computer so I can install/update/fix it as needed. 

If I could get some help on how to go about this it would be great. Can I get this so I can control their desktop or is it going to be terminal only?

Thanks for the help.

---

### Post by CaptSaltyJack on 2008-11-07
[http://ubuntuforums.org/showthread.php?t=905200](http://ubuntuforums.org/showthread.php?t=905200)

NoMachine is the way to go for remote access (to a graphical desktop).

---

### Post by adlin5000 on 2008-11-07
Thanks. I think thats just what I was looking for. I really had no idea of where to start. Even doing a search here for "remote access" did not bring up anything useful.

---

### Post by CaptSaltyJack on 2008-11-07
Keep in mind, NoMachine lets you log into your own session remotely, which does not interfere at all with the person sitting at the computer, great if you want to just log in, update some software, and leave.  VNC, however, would let you actually log in and see what your friend is doing (moving their mouse around, typing) if that's what you're after.

But like I say in the link above, NoMachine is leagues ahead of VNC on performance.

---

### Post by Youresorock on 2008-11-07
Personally, I'd do it the built-in way: SSH.

If you can forward port 22 you can remote in and do everything you need.  You can even do a full Gnome session, although that would be slow over the internet.  

Just install OpenSSH server on the remote machine, and forward port 22.

---

### Post by CaptSaltyJack on 2008-11-07
Yes, I prefer ssh too.  Just wasn't sure if he was looking for a command-line route or not.

Forgot to mention, NoMachine/NX requires SSH anyway, so you'll have to install that first. (sudo apt-get install ssh)

---

### Post by adlin5000 on 2008-11-07
Its good to have know all three options (NX/VNC/terminal). NX for if I just want to hop in and update, VNC if I need to show them how to do something, and terminal because sometimes thats the easiest (or only) way to get stuff done. And besides, the more I know the better. Thanks.

---

### Post by Peter09 on 2008-11-07
NX will allow you to view and control a users desktop, it depends how you configure it.

---

### Post by CaptSaltyJack on 2008-11-07
Actually, best way to just apply updates: ssh into the computer, then "sudo apt-get update", "sudo apt-get upgrade", done.

NX is good for messing around with apps you can only get to via the desktop. (that have a graphical interface)

---

### Post by CaptSaltyJack on 2008-11-07
> **Peter09 said:**
> NX will allow you to view and control a users desktop, it depends how you configure it.

No kidding??  I never knew that, do you have a link to somewhere that describes how to set that up?

---

### Post by Peter09 on 2008-11-07
If you go into /usr/NX/etc/server.cfg there is a whole section on desktop sharing.

I think that if you have a desktop open it will connect to that.

---

### Post by CaptSaltyJack on 2008-11-07
Wow, yeah, lots of options for desktop sharing there, didn't even know about that - thanks!

---

