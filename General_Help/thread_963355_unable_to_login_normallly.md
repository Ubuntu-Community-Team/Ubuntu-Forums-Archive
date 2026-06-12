---
title: "unable to login normallly"
date: 2008-10-30
forum: General Help
---

### Post by oyvindm on 2008-10-30
Hi!

I'm new to the whole linux experience. Have had ubuntu for approximatly one month now and it's worked great.

But yesterday I was fiddling around with some windows games (Age of Empires 2) and som iso handlers when my pc started operating really slow. So I shut it off, and when I turned it back on I couldn't login. Well I could login, it just couldn't open anything. So I tried the Failsafe Gnome variant and was told that I couldn't login there either.

It tells me that it isn't allowed access to any of the /tmp files or folders. (gconfd-myname and gconfd-root aswell as orbit-myname and orbit-root)

As usual, I was probably a bit hasty in my attempt at getting Age of Empires running and extracted som files to the /tmp folder. So in my head this is probably the reason why it's all screwed up now. But I've logged in via the Failsafe terminal function and have deleted everything in there that "shouldn't" be there. It still didn't work. i've also deleted everything that was in there, so that what is there now has been created automatically by the system...

so... Any ideas? i'm not that comfortable with the terminal but i'm getting there. i've got to connect to the wired network and don't know how to do it in terminal (802.1x protected wired connection) so it's a bit hard to just copy over info and paste it here (I'm now running ubuntu from the cd).

well anyway. all tips and help are much appreciated! really.

øyvind

---

### Post by geirha on 2008-10-30
What's the permissions on the /tmp directory?
```
ls -ld /tmp
```

---

### Post by oyvindm on 2008-10-30
I'll check it out. 

I have to go to class, so I'll post it when I get back.

thanks for a quick response!

---

### Post by oyvindm on 2008-10-30
hi again.

the output read:

drwxr-xr-x 9 root root 4096 <date&time> /tmp

which I guess means that its only root...

---

### Post by geirha on 2008-10-30
Yes, only root may write to /tmp with those permissions. Any idea how it got the wrong permissions set? 

All users should have full access to /tmp, plus it should have the sticky-bit, so ```
sudo chmod 1777 /tmp
``` should set it right.

---

### Post by oyvindm on 2008-10-30
thanks! I'll try it out.

I have no idea why it's been set to root. What I was doing and what I did is stated in the first post...

øyvind

edit:
by the way, would you mind explaining the code you gave me? so chmod changes the permission settings of files and folders? and 1777 is the code for an "open" permisssion setting? if so, how do I find out what the permission codes are?

thanks again.

---

### Post by oyvindm on 2008-10-30
woohoo!

it worked!

first time I got to log in again I got a ton of error messages concerning me deleting all the /tmp files. and I only got a very non-graphical desktop. but now I'm back in and everything seems fine til now.

so thank you very much indeed!

---

### Post by geirha on 2008-10-30
> **oyvindm said:**
> thanks! I'll try it out.

I have no idea why it's been set to root. What I was doing and what I did is stated in the first post...

øyvind

edit:
by the way, would you mind explaining the code you gave me? so chmod changes the permission settings of files and folders? and 1777 is the code for an "open" permisssion setting? if so, how do I find out what the permission codes are?

thanks again.
The wiki has a page explaining file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

It doesn't mention the sticky bit though (which is the 1 in 1777). The 777 part gives everyone read, write and execute permissions, so any user may create files in /tmp. The sticky-bit makes it so that if user user1 creates a file in /tmp, only user1 may delete it again. (without the sticky-bit everyone can delete any files in /tmp)

Also note that the contents of /tmp is wiped every time you boot, so don't put anything you want to keep in there.

---

